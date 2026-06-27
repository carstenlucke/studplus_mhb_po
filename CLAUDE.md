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
   Bei **manchen** Handbüchern erfasst `pdftotext` die Ankreuz-Checkboxen als Glyphen (`☒` = gesetzt,
   `☐` = leer) — dann sind sie für Pflicht/Wahlpflicht, Fachrichtung, Sprache, Dauer, Häufigkeit,
   Bonuspunkte und Lehrveranstaltungsart **maßgeblich**. **ABER:** das ist NICHT garantiert.
   **Immer zuerst prüfen:** `grep -c "☒\|☐" full_layout.txt`. Ist das Ergebnis **0**, fehlen die
   Checkboxen im Text → die betroffenen Felder **müssen aus den Seitenbildern** gelesen werden
   (siehe §8). In diesem Fall die Modul-Agenten explizit anweisen, Ankreuzfelder am Bild zu lesen.
   SWS-Zahlenwerte (z. B. „0 SWS 4 SWS …") stehen i. d. R. trotzdem im Text.
3. **Seitenbilder rendern:** `pdftoppm -png -r 130 "<pdf>" img/page` → `page-01.png`/`page-001.png`
   (3-stellig ab 100 Seiten). Pflicht-Rückfallebene für unleserliche/mehrdeutige Felder — und
   **obligatorisch** für alle Checkbox-Felder, wenn Schritt 2 keine Glyphen findet.
4. **Module finden & Manifest bauen:** `grep -n "^[[:space:]]*Modulcode" full_layout.txt`
   (bzw. in Python `l.lstrip().startswith("Modulcode")`). **Wichtig:** `Modulcode`-Zeilen sind
   manchmal **eingerückt** — ein striktes `^Modulcode` übersieht sie und bündelt fremde Module in
   Nachbar-Slices! Gegenprobe: `grep -c "Modulcode"` (irgendwo in Zeile) muss zur Zahl der erkannten
   Modulstarts passen. **Nicht** das Inhaltsverzeichnis zur Modulauflistung verwenden — es ist oft
   **veraltet/unvollständig**. Maßgeblich ist die Zahl der `Modulcode`-Vorkommen im Modulteil; zur
   Plausibilisierung zusätzlich gegen den Web-Verlaufsplan zählen.
   Jedes Modul beginnt mit `Modulcode`; das Modul endet eine Zeile vor dem nächsten `Modulcode`
   (letztes Modul: Dateiende). Daraus ein **Manifest** je Modul:
   `code, slug, titel_de, startzeile, endzeile, modultyp, fachrichtungen, studiensemester,
   pdf_seiten`. Die PDF-Seiten je Modul über die Form-Feed-Zeichen (`\f`) im Layout-Text zählen.
   Codes müssen nicht numerisch/eindeutig sein (z. B. wörtlich `NEU`, Doppelcodes wie `80001/80002`).
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
   - Autoritative Felder (`modulcode`, `titel_de`, `modultyp`, `studiensemester`; bei Text-Checkboxen
     auch `fachrichtungen`) aus dem geprüften Manifest als **fix** an die Agenten geben, Rest
     extrahieren sie aus Text bzw. Bild. Sind die Checkboxen nur im Bild (§8), lesen die Agenten
     `fachrichtungen` selbst aus dem Seitenbild.
   - **Manifest im Skript einbetten, NICHT über `Workflow`-`args`:** Der `args`-Wert kommt im Skript
     u. U. nicht als Array an (`MODULES.map is not a function`). Das Manifest-Array direkt als
     JS-Literal in den Skripttext schreiben (oder defensiv `JSON.parse`). Bei vielen Modulen das
     kompakte Array per Skript erzeugen und in den Workflow-Skripttext einsetzen.
8. **Index & Rohmaterial:** `README.md` schreiben (siehe §6) und Quell-PDF nach `quellen/` kopieren.
9. **Validieren** (§7): Frontmatter-/Sektions-Check über alle Dateien; Dateizahl == Modulanzahl;
   **CrP-Plausibilität** gegen die Soll-Gesamtsumme des Studiengangs (Master Prozessmanagement:
   3 × 30 = **90**; Bachelor Softwaretechnologie: 7 Semester = **210**, mit vertiefungsabhängigem
   Pfad). Geht es nicht auf → Modulbestand/Klassifikation prüfen.

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
- **Checkboxen sind maßgeblich** — aber **Quelle je Handbuch prüfen!** `☒` = gesetzt, `☐` = leer.
  Daraus Pflicht/Wahlpflicht (über „Verwendbarkeit"), Fachrichtung/Vertiefung, Sprache, Dauer,
  Häufigkeit, Bonuspunkte, Lehrveranstaltungsart. Stehen die Glyphen **nicht** im Textextrakt
  (`grep -c "☒\|☐"` = 0), sind diese Felder **ausschließlich aus den Seitenbildern** zu lesen; die
  Agenten dann explizit darauf hinweisen (und dass pro Seite mehrere Module stehen können).
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

- **Eingerückte `Modulcode`-Zeilen:** In manchen Handbüchern beginnt die `Modulcode`-Zeile **nicht**
  in Spalte 0. Ein striktes `^Modulcode` übersieht solche Module, deren Inhalt dann in das
  vorherige Modul-Slice „durchsickert" (Agenten melden „fremde Module auf der Seite"). Immer
  einrückungstolerant matchen (`^[[:space:]]*Modulcode` / `lstrip().startswith`) und die Trefferzahl
  gegen `grep -c "Modulcode"` und den Web-Verlaufsplan gegenprüfen. _(Konkret aufgetreten: SWT-B.Sc.
  hatte 47 statt vermeintlich 41 Module.)_
- **Checkboxen fehlen im Textextrakt:** Je nach PDF rendert `pdftotext` die `☒/☐`-Glyphen gar nicht
  (`grep -c "☒\|☐"` = 0). Dann Fachrichtung/Vertiefung, Sprache, Dauer, Häufigkeit, Bonuspunkte und
  Lehrveranstaltungsart **aus den Seitenbildern** lesen lassen. SWS-Zahlen stehen meist trotzdem im
  Text.
- **Mehrere Module pro Seite / Modulgrenzen mitten auf der Seite:** Beim Bild-Lesen genau auf den
  Block des eigenen Moduls achten (beginnt mit dessen Modulcode/Modulbezeichnung); Felder von
  Nachbarmodulen ignorieren.
- **Nicht-numerische/doppelte Modulcodes:** Codes können wörtlich `NEU` lauten (noch nicht final
  vergeben) oder doppelt sein (z. B. `80001/80002` für ein über zwei Semester laufendes Modul, oder
  derselbe Code für zwei verschiedene Module). Codes für Dateinamen sanitisieren (`/`→`-`), Kollision
  über unterschiedliche Slugs auflösen und im README dokumentieren.
- **Vertiefungsspezifische Pflichtmodule:** „Pflichtmodul" heißt nicht zwingend „für alle
  Fachrichtungen". Manche Pflichtmodule sind nur in **einer** Vertiefung angekreuzt — `fachrichtungen`
  modulgenau aus der Quelle übernehmen, nicht pauschal „alle" setzen.
- **`Workflow`-`args` nicht als Array:** Manifest direkt im Skript einbetten statt über `args`
  übergeben (siehe §3 Schritt 7).
- **Studiengangsname variiert** (z. B. „Softwaretechnik" vs. „Softwaretechnologie"): kanonische Form
  festlegen, Abweichung notieren.
- **Bachelor ≠ Master:** mehr Semester (oft 7), höhere CrP-Gesamtsumme (z. B. 210), „Fachrichtungen"
  heißen ggf. „Vertiefungsrichtungen", Praxisphasen/Projektstudium/Thesis mit Sonder-CrP und teils
  ohne Präsenz-SWS; Semesterangaben können Bereiche sein (`1./2.`, `3./4.`).
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
