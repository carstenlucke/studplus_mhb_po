---
description: Extrahiert ein Modulhandbuch-PDF konform zum Repo-Playbook in strukturierte Markdown-Modul-Dateien + Index
argument-hint: <pdf-pfad> [website-url]
---

Extrahiere ein Modulhandbuch **streng nach dem Playbook in `CLAUDE.md`** (Repo-Root, Schritte §1–§9,
Modul-Vorlage §4, Regeln §5). Erzeuge die dort definierte konforme Ergebnisstruktur.

## Eingaben
- **PDF (Pflicht):** `$1`
- **Website (optional):** `$2` — Studiengangsseite mit den Studienverlaufsplänen je Fachrichtung.

Wenn `$1` leer/nicht angegeben ist: **abbrechen** und den PDF-Pfad erfragen. Prüfe vor Beginn, dass
die Datei existiert (`pdfinfo "$1"`).

## Auftrag

1. **Zielnamen ableiten:** Aus `pdfinfo`/PDF-Titel den Studiengang + Version/Fassungsdatum bestimmen
   und daraus
   - Ergebnis-Ordner `modulhandbuch-<studiengang-slug>/` (mit `module/`, `quellen/`),
   - PDF-Zielnamen `Modulhandbuch_<Studiengang>_V<version>_<JJJJ-MM-TT>.pdf`
   bilden (Slug-/Namensregeln §9). Bei Unklarheit zum Slug **kurz rückfragen**.

2. **Quelle aufbereiten** (Zwischendateien ins Scratchpad, **nicht** ins Repo):
   `pdftotext -layout "$1" full_layout.txt` · `pdftoppm -png -r 130 "$1" img/page`.
   Die Checkbox-Zeichen `☒`/`☐` im Text sind **maßgeblich** (§5).

   **Checkbox-Check:** `grep -c "☒\|☐" full_layout.txt`. Ergebnis **0** → Checkboxen fehlen im Text;
   alle Ankreuzfelder müssen aus den Seitenbildern gelesen werden (Agenten entsprechend anweisen).

3. **Module + Manifest:** `grep -n "^[[:space:]]*Modulcode" full_layout.txt` (einrückungstolerant —
   striktes `^Modulcode` übersieht eingerückte Codes!). Trefferzahl gegen `grep -c "Modulcode"` und
   den Web-Verlauf gegenprüfen. Modulgrenzen = von `Modulcode` bis vor das nächste `Modulcode`.
   Manifest je Modul bauen (`code, slug, titel_de, zeilen, modultyp, studiensemester, pdf_seiten`;
   `fachrichtungen` nur wenn Checkboxen im Text, sonst von Agenten aus Bild) und Text in
   `modtext/<code>-<slug>.txt` splitten (Form-Feeds entfernen). Codes für Dateinamen sanitisieren
   (`/`→`-`; auch `NEU`/Doppelcodes möglich).

4. **Klassifikation prüfen:**
   - Pflicht/Wahlpflicht, Fachrichtung, Semester primär aus den PDF-Checkboxen („Verwendbarkeit");
     fehlen die Checkboxen im Text, aus den Seitenbildern. „Pflichtmodul" ≠ zwingend „alle
     Fachrichtungen" (vertiefungsspezifische Pflichtmodule kommen vor).
   - **Falls `$2` angegeben:** die Seite (und ggf. die Fachrichtungs-Unterseiten) abrufen, die
     aufklappbaren Verlaufspläne extrahieren und gegen die PDF-Klassifikation cross-checken;
     Abweichungen dokumentieren.
   - **Falls `$2` fehlt:** ausschließlich aus dem PDF klassifizieren und im README vermerken, dass
     kein Web-Abgleich erfolgte.

5. **Orchestrieren via `Workflow`** (Subagenten, Hauptkontext schlank halten):
   - optional **1 Web-Agent** (nur wenn `$2` gegeben) → Verlaufspläne strukturiert (bei verweigertem
     Zugriff `available:false` → README fällt auf PDF-Daten zurück);
   - **N Modul-Agenten parallel**: jeder liest seine Text-Slice, füllt **exakt die Vorlage aus
     CLAUDE.md §4**, schreibt `module/<code>-<slug>.md`, gibt nur kompakte Zusammenfassung +
     Anomalien zurück (`schema`-validiert). Vorlage **einmal** im Skript definieren und an **alle**
     Agenten identisch übergeben. Autoritative Felder (`modulcode`, `titel_de`, `modultyp`,
     `studiensemester`; `fachrichtungen` nur bei Text-Checkboxen) aus dem geprüften Manifest fix
     vorgeben.
   - **Manifest direkt im Workflow-Skript einbetten** (JS-Literal), NICHT über `args` — `args` kommt
     u. U. nicht als Array an.

6. **Index & Rohmaterial:** `README.md` mit den Pflichtinhalten aus §6 schreiben (Verlaufspläne je
   Fachrichtung mit CrP-Summen, Pflicht-/Wahlpflicht-Tabellen, Datenqualitäts-Hinweise) und das
   Quell-PDF nach `quellen/` kopieren; im README darauf verlinken.

7. **Validieren (§7):** Anzahl `module/*.md` == Anzahl `Modulcode`; Frontmatter-/Sektions-Check über
   alle Dateien; CrP-Summen je Fachrichtung gegen die Soll-Gesamtsumme (typ. 90) prüfen.

## Beachte
- Inhalte **wortgetreu & vollständig**; nur OCR-/Trennungsfehler behutsam korrigieren; Original-
  Eigenheiten erhalten; fehlende Abschnitte weglassen — nichts erfinden (§5).
- **Bekannte Stolperfallen (§8):** eingerückte `Modulcode`-Zeilen (sonst Module übersehen!),
  Checkboxen nur im Bild, mehrere Module pro Seite, doppelte/nicht-numerische Codes (`NEU`,
  `80001/80002`), vertiefungsspezifische Pflichtmodule, `Workflow`-`args`, Web-/PDF-Schreibvarianten,
  Bachelor ≠ Master (mehr Semester, andere CrP-Summe).

Abschließend: kurze Zusammenfassung (Anzahl Module, Pfad zum `README.md`, offene Datenqualitäts-
Punkte).
