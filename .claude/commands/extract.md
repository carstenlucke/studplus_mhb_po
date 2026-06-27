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

3. **Module + Manifest:** `grep -n -A2 "^Modulcode" full_layout.txt`; Modulgrenzen = von `Modulcode`
   bis vor das nächste `Modulcode`. Manifest je Modul bauen (`code, slug, titel_de, zeilen,
   modultyp, fachrichtungen, studiensemester, pdf_seiten`) und Text in `modtext/<code>-<slug>.txt`
   splitten (Form-Feeds entfernen).

4. **Klassifikation prüfen:**
   - Pflicht/Wahlpflicht, Fachrichtung, Semester primär aus den PDF-Checkboxen („Verwendbarkeit").
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
     `fachrichtungen`, `studiensemester`) aus dem geprüften Manifest fix vorgeben.

6. **Index & Rohmaterial:** `README.md` mit den Pflichtinhalten aus §6 schreiben (Verlaufspläne je
   Fachrichtung mit CrP-Summen, Pflicht-/Wahlpflicht-Tabellen, Datenqualitäts-Hinweise) und das
   Quell-PDF nach `quellen/` kopieren; im README darauf verlinken.

7. **Validieren (§7):** Anzahl `module/*.md` == Anzahl `Modulcode`; Frontmatter-/Sektions-Check über
   alle Dateien; CrP-Summen je Fachrichtung gegen die Soll-Gesamtsumme (typ. 90) prüfen.

## Beachte
- Inhalte **wortgetreu & vollständig**; nur OCR-/Trennungsfehler behutsam korrigieren; Original-
  Eigenheiten erhalten; fehlende Abschnitte weglassen — nichts erfinden (§5).
- **Bekannte Stolperfallen (§8):** doppelte Modulcodes (getrennte Dateien + Hinweis), Wahlpflicht
  ohne Fachrichtungs-Checkboxen, mehrere Kreuze in der KapVO-Zeile, Projektphasen/Thesis,
  Web-/PDF-Schreibvarianten.

Abschließend: kurze Zusammenfassung (Anzahl Module, Pfad zum `README.md`, offene Datenqualitäts-
Punkte).
