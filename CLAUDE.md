# Playbook: Modulhandbücher strukturiert extrahieren

Dieses Repository sammelt strukturierte, KI-agenten-taugliche Aufbereitungen von
**Modulhandbüchern** (StudiumPlus / THM-ZDH). Diese Datei beschreibt das **verbindliche Vorgehen**,
damit **weitere** Modulhandbücher exakt **konform** zur bestehenden Aufbereitung extrahiert werden.

> **Referenzimplementierung:** [`modulhandbuch-prozessmanagement/`](./modulhandbuch-prozessmanagement/)
> (Masterstudiengang Prozessmanagement). An dieser Struktur, Vorlage und Namensgebung orientieren
> sich alle weiteren Studiengänge 1:1.

---

## 1. Ergebnis-Konvention (Verzeichnisstruktur)

Pro Studiengang **ein** Top-Level-Ordner `modulhandbuch-<studiengang-slug>/`:

```
modulhandbuch-<studiengang>/
├── README.md          # Index: Studiengangsüberblick, Verlaufspläne je Fachrichtung, Modullisten, Links
├── module/            # je Modul eine Datei  <modulcode>-<slug>.md
│   └── 1003-controlling.md …
└── quellen/           # Originaldokument(e) als Rohmaterial (PDF)
    └── Modulhandbuch_<Studiengang>_V<n>_<JJJJ-MM-TT>.pdf
```

- **Eine Markdown-Datei pro Modul** mit identischem Aufbau (siehe Vorlage §4).
- **Eine `README.md`** als Einstieg, die alle Modul-Dateien verlinkt.
- **Das Quell-PDF** wird unter `quellen/` mitversioniert (sprechender, datierter Dateiname).

---

## 2. Voraussetzungen (Tools)

Die Extraktion arbeitet **PDF-text-basiert** (nicht reine OCR), Seitenbilder dienen nur der
Verifikation. Benötigt (alle vorhanden via Homebrew):

| Tool | Zweck |
| --- | --- |
| `pdfinfo` | Seitenzahl/Metadaten prüfen |
| `pdftotext -layout` | **Primärquelle** – Layout-Text inkl. der Checkbox-Zeichen `☒`/`☐` |
| `pdftoppm -png -r 130` | Seitenbilder rendern (Verifikation im Zweifel) |
| `python3` | Modul-Split, Manifest, Validierung |

Arbeitsdateien (Volltext, Seitenbilder, Text-Slices, Manifest) gehören in ein **temporäres
Arbeitsverzeichnis** (Scratchpad), **nicht** ins Repo. Ins Repo kommen nur `README.md`,
`module/*.md` und `quellen/*.pdf`.

---

## 3. Ablauf (Schritt für Schritt)

1. **PDF prüfen:** `pdfinfo "<pdf>"` → Seitenzahl, Titel, Fassung/Version notieren.
2. **Volltext extrahieren:** `pdftotext -layout "<pdf>" full_layout.txt`.
   Die `pdftotext`-Ausgabe erfasst **die Ankreuz-Checkboxen zuverlässig** (`☒` = gesetzt,
   `☐` = leer). Diese sind für Pflicht/Wahlpflicht, Fachrichtung, Sprache, Dauer, Häufigkeit,
   Bonuspunkte und Lehrveranstaltungsart **maßgeblich**.
3. **Seitenbilder rendern:** `pdftoppm -png -r 130 "<pdf>" img/page` → `page-01.png` … nur als
   Rückfallebene, wenn ein Feld im Text unleserlich/mehrdeutig ist.
4. **Module finden & Manifest bauen:** `grep -n -A2 "^Modulcode" full_layout.txt`.
   **Nicht** das Inhaltsverzeichnis zur Modulauflistung verwenden — es ist erfahrungsgemäß oft
   **veraltet/unvollständig** (listet nicht alle Module, falsche Seitenzahlen). Maßgeblich für die
   Vollständigkeit ist die Zahl der `Modulcode`-Vorkommen im Modulteil, nicht das Verzeichnis.
   Jedes Modul beginnt mit `Modulcode`; das Modul endet eine Zeile vor dem nächsten `Modulcode`
   (letztes Modul: Dateiende). Daraus ein **Manifest** je Modul:
   `code, slug, titel_de, startzeile, endzeile, modultyp, fachrichtungen, studiensemester,
   pdf_seiten`. Die PDF-Seiten je Modul über die Form-Feed-Zeichen (`\f`) im Layout-Text zählen.
5. **Klassifikation gegen die Webseite gegenprüfen** (Pflicht vs. Wahlpflicht, Fachsemester,
   Fachrichtungs-Zuordnung). Studiengangsseite + Unterseiten der Fachrichtungen abrufen; die
   aufklappbaren **Studienverlaufspläne** stecken im HTML. Beispiel Prozessmanagement:
   `…/prozessmanagement/`, `…/prozessmanagement-steuerung-von-geschaeftsprozessen/`,
   `…/prozessmanagement-technische-prozesse/`. Die PDF-Checkboxen sind die Primärquelle; die
   Webseite bestätigt/ergänzt Semesterlage und fachrichtungsspezifische Module.
6. **Text je Modul splitten:** per Zeilenbereich in saubere Einzeldateien
   `modtext/<code>-<slug>.txt` schneiden (Form-Feeds entfernen). So bekommt jeder Agent eine
   verlustfreie, kontextarme Einzelquelle.
7. **Orchestrieren via `Workflow`** (Subagenten, damit der Hauptkontext schlank bleibt):
   - **1 Web-Agent**: ruft die Fachrichtungs-Seiten ab und liefert die Verlaufspläne strukturiert
     zurück (bei verweigertem Web-Zugriff: `available:false` → README fällt auf PDF-Daten zurück).
   - **N Modul-Agenten parallel** (`parallel(...)`): jeder liest seine Text-Slice, füllt **exakt
     die Vorlage aus §4**, schreibt `module/<code>-<slug>.md` und gibt nur eine **kompakte
     Zusammenfassung** + Anomalien zurück (`schema`-validiert). Die Vorlage wird **einmal** im
     Skript definiert und an **alle** Agenten identisch übergeben → garantierte Konsistenz.
   - Autoritative Felder (`modulcode`, `titel_de`, `modultyp`, `fachrichtungen`, `studiensemester`)
     aus dem geprüften Manifest als **fix** an die Agenten geben, Rest extrahieren sie aus dem Text.
8. **Index & Rohmaterial:** `README.md` schreiben (siehe §6) und Quell-PDF nach `quellen/` kopieren.
9. **Validieren** (§7): Frontmatter-/Sektions-Check über alle Dateien **und** CrP-Summen je
   Fachrichtung gegen die Soll-Gesamtsumme (typ. 3 × 30 = **90 CrP**) prüfen.

---

## 4. Modul-Vorlage (VERBINDLICH – identisch für jedes Modul)

YAML-Frontmatter (maschinenlesbar) + lesbarer Body. Reihenfolge und Überschriften **nicht** ändern.
Werte in `<…>` aus der Quelle füllen; fehlende Abschnitte **weglassen** (nichts erfinden).

```markdown
---
modulcode: "<code>"
titel_de: "<deutsche Bezeichnung>"
titel_en: "<englische Bezeichnung; falls keine: gleicher Wert oder \"\">"
modultyp: "Pflichtmodul"            # oder "Wahlpflichtmodul"
studiensemester: <1|2|3>
fachrichtungen:
  - "Steuerung von Geschäftsprozessen"
  - "Technische Prozesse"           # nur die zutreffende(n); bei Wahlpflicht i.d.R. beide
dauer_semester: <1|2>
haeufigkeit: "<jährlich|semesterweise|bei Bedarf>"
sprache: "<Deutsch | Englisch | \"Deutsch, Englisch\">"
crp: <Zahl>
arbeitsaufwand_h: <Zahl>
praesenzzeit_h: <Zahl>
selbststudium_h: <Zahl>
modulverantwortliche: "<Name(n)>"
lehrende:
  - "<Name>"                        # je Person ein Eintrag; auch "Projektorientiert"/"Coaching"
voraussetzungen_notwendig: "<Text|keine>"
voraussetzungen_empfohlen: "<Text|keine>"
bonuspunkte: <true|false>           # true nur wenn ☒ Ja
pruefungsvorleistungen: "<Text|keine>"
pruefungsleistungen: "<Text, z.B. Klausur (90 Minuten)>"
lehr_lernformen: "<z.B. Seminaristischer Unterricht>"
lehrveranstaltungsart: "<Vorlesung|Seminar|Übung|Praktikum|Thesis|BPP>"   # die angekreuzte Art
sws:
  vorlesung: <Zahl>
  seminar: <Zahl>
  uebung: <Zahl>
  praktikum: <Zahl>
  thesis: <Zahl>
  bpp: <Zahl>
---

# <titel_de>

**Modulcode:** <code> · **Typ:** <modultyp> · **Semester:** <n> · **CrP:** <crp>

- **Englischer Titel:** <titel_en>
- **Fachrichtungen:** <kommagetrennt>   # bei Wahlpflicht: Zusatz "_(Wahlpflichtbereich – für beide Fachrichtungen wählbar)_"
- **Modulverantwortliche:** <…>
- **Lehrende:** <kommagetrennt>
- **Sprache:** <…> · **Häufigkeit:** <…> · **Dauer:** <n> Semester

## Arbeitsaufwand
| Arbeitsaufwand | Präsenzzeit | Selbststudium |
| --- | --- | --- |
| <a> h | <b> h | <c> h |

## Voraussetzungen
- **Notwendig:** <…>
- **Empfohlen:** <…>

## Prüfung
- **Prüfungsvorleistungen:** <…>
- **Prüfungsleistungen:** <…>
- **Bonuspunkte:** <ja|nein>

## Kurzbeschreibung
**Deutsch:** <…>

**English:** <…>      # weglassen, wenn nicht vorhanden

## Inhalte
<Bulletpoints; falls Quelle Fließtext, als Absatz wiedergeben>

## Qualifikationsziele und angestrebte Lernergebnisse
<optionale einleitende "Die Studierenden …"-Liste, danach nur vorhandene Unterabschnitte:>
### Fachkompetenzen
<…>
### Methodenkompetenzen
<…>
### Sozialkompetenzen
<…>
### Selbstkompetenzen
<…>

## Lehr- und Lernformen
<lehr_lernformen> — Art der Lehrveranstaltung nach KapVO: <lehrveranstaltungsart> (<SWS> SWS)

## Literatur, Medien
<Bulletpoints; Angaben wie "themenbezogen" wörtlich; Abschnitt weglassen wenn nicht vorhanden>

---
*Quelle: Modulhandbuch <Studiengang> (M.Sc.), THM-ZDH, Version <n> (Fassung vom <Datum>), Modulcode <code>, S. <p0>–<p1>.*
```

---

## 5. Extraktionsregeln

- **Wortgetreu & vollständig.** Inhalte, Listen und Kompetenztexte vollständig übernehmen, nicht
  kürzen, nicht paraphrasieren.
- **Checkboxen sind maßgeblich.** `☒` = gesetzt, `☐` = leer. Daraus Pflicht/Wahlpflicht (über
  „Verwendbarkeit"), Fachrichtung, Sprache, Dauer, Häufigkeit, Bonuspunkte, Lehrveranstaltungsart.
- **OCR-/Trennungsfehler** (Silbentrennung am Zeilenumbruch, fehlende/überzählige Leerzeichen)
  behutsam korrigieren. **Inhaltliche Eigenheiten/Tippfehler des Originals bleiben erhalten** –
  im Zweifel wörtlich übernehmen und als Anomalie melden.
- **Deutsche Sonderzeichen** (ä ö ü ß) korrekt erhalten.
- **Fehlende Abschnitte weglassen**, fehlende Frontmatter-Werte als `""`/`null` – nichts erfinden.
- **Störzeilen ignorieren:** blanke Seitenzahlen, übergelaufene Abschnittsüberschriften
  („Pflichtmodule:", „Wahlpflichtmodule:").
- **Jede Anomalie/Mehrdeutigkeit melden** (Subagent-Rückgabe) und – sofern strukturrelevant – in
  den README-Abschnitt „Hinweise zur Datenqualität" aufnehmen.

---

## 6. README-Index (Pflichtinhalte)

1. **Kopf:** Abschluss, Regelstudienzeit, CrP-Gesamt, Fachrichtungen, Quellenangabe inkl. Link auf
   das PDF unter `quellen/`.
2. **Verwendungshinweis** (Frontmatter-Felder erklärt) für KI-Agenten.
3. **Studienverlaufsplan je Fachrichtung** als Tabelle (Sem · Modul (verlinkt) · Code · CrP · Typ)
   mit Semester-Summen und Gesamtsumme; „Wahlpflichtfach"-Slot kenntlich machen.
4. **Pflichtmodul-Übersicht** und **Wahlpflichtmodul-Übersicht** (Tabellen mit Links).
5. **Hinweise zur Datenqualität** (strukturrelevante Anomalien, s. §7).

---

## 7. Qualitätssicherung

- **Vollständigkeit:** Anzahl `module/*.md` == Anzahl `Modulcode`-Vorkommen im PDF.
- **Frontmatter-/Sektions-Check** (Skript) über alle Dateien: Pflichtfelder vorhanden, alle
  Pflicht-Sektionen vorhanden, Quellen-Footer vorhanden.
- **CrP-Plausibilität:** Pro Fachrichtung müssen die CrP je Semester die Soll-Summe ergeben
  (typ. 30/30/30 = 90). Geht das nicht auf → Klassifikation/Fachrichtungs-Zuordnung prüfen.
- **Cross-Check Web ↔ PDF:** fachrichtungsspezifische Module und Semesterlage müssen
  übereinstimmen; Abweichungen dokumentieren.

---

## 8. Bekannte Stolperfallen

- **Inhaltsverzeichnis ist unzuverlässig:** Das TOC im PDF ist nicht immer aktuell/aussagekräftig
  und listet häufig **nicht alle** Module (bzw. mit falschen Seitenzahlen). Modulbestand,
  Reihenfolge und Seiten daher **immer** aus den `Modulcode`-Vorkommen im Modulteil ableiten,
  nie aus dem Verzeichnis.
- **Doppelte Modulcodes:** Codes können in der Quelle mehrfach vergeben sein (z.B. zwei Module mit
  `2004`). Beide als **getrennte Dateien** mit unterschiedlichem Slug anlegen
  (`2004-<slug-a>.md`, `2004-<slug-b>.md`) und die Kollision im README dokumentieren.
- **Wahlpflichtmodule ohne Fachrichtungs-Checkboxen:** Bei „Verwendbarkeit" steht nur
  „Wahlpflichtmodul …" ohne Fachrichtungs-Ankreuzung → `modultyp: Wahlpflichtmodul`, Fachrichtungen
  aus dem Verlaufsplan (i.d.R. für beide wählbar) setzen.
- **Mehrere Kreuze in der KapVO-Zeile:** maßgeblich ist die SWS-tragende Art (>0 SWS); zusätzliche
  Kreuze (oft „Thesis") als versehentlichen Marker behandeln und vermerken.
- **Projektphasen / Thesis:** „Coaching"/projektorientiert, oft ohne Präsenz-SWS, abweichende CrP
  (z.B. 10/10/20). Lehrende-Feld kann „Projektorientiert" lauten.
- **Seitenumbrüche** zerschneiden Modul-Tabellen mehrfach; der zeilenbasierte Split je `Modulcode`
  fängt das ab. Form-Feeds (`\f`) vor dem Speichern aus den Slices entfernen.
- **Schreibvarianten Web vs. PDF** (z.B. „Human Ressource" vs. „Human Resource"): die
  **Modulhandbuch-Schreibweise** ist maßgeblich; Abweichung notieren.

---

## 9. Namens- & Slug-Konventionen

- Dateiname: `<modulcode>-<slug>.md`. Slug = Modultitel, klein, ASCII-nah, Bindestriche statt
  Leerzeichen, Umlaute aufgelöst (ä→ae, ö→oe, ü→ue, ß→ss), Sonderzeichen entfernt; bei sehr langen
  Titeln sinnvoll kürzen (Kernbegriffe).
- Quell-PDF: `Modulhandbuch_<Studiengang>_V<version>_<JJJJ-MM-TT>.pdf` (Datum = Fassungsdatum).
