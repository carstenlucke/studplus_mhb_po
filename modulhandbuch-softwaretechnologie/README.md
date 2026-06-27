# Modulhandbuch – Bachelorstudiengang Softwaretechnologie (B.Sc.)

Strukturierte, KI-agenten-taugliche Aufbereitung aller Module des dualen, praxisintegrierten Bachelorstudiengangs **Softwaretechnologie (B.Sc.)** des Wissenschaftlichen Zentrums Duales Hochschulstudium (ZDH) der **Technischen Hochschule Mittelhessen (THM)** / **StudiumPlus**.

- **Abschluss:** Bachelor of Science (B.Sc.)
- **Regelstudienzeit:** 7 Semester (dual, praxisintegriert)
- **Umfang:** 210 CrP (ECTS)
- **Vertiefungsrichtungen:** Data Science · IT-Security · Softwareentwicklung
- **Module:** 47 (36 Pflicht / 11 Wahlpflicht)

> **Quellen**
> - Modulhandbuch zur Prüfungsordnung des ZDH der THM für den dualen Bachelorstudiengang Softwaretechnologie (B.Sc.), **Version 4**, Fassung vom **11. Dezember 2024** (PDF, 104 Seiten) — Originaldokument unter [`quellen/Modulhandbuch_Softwaretechnologie_Bachelor_V4_2024-12-11.pdf`](./quellen/Modulhandbuch_Softwaretechnologie_Bachelor_V4_2024-12-11.pdf).
> - Studiengangsseite THM/StudiumPlus (Studienverlauf), abgerufen 06/2026: [Seite zum Studiengang](https://www.thm.de/site/studium/unsere-studienangebote/softwaretechnologie-bachelor-bsc-praxisintegriert-dual-studiumplus.html)

---

## Verwendung (für KI-Agenten & Menschen)

Jedes Modul liegt als eigene Markdown-Datei im Ordner [`module/`](./module/) und folgt derselben Struktur: **YAML-Frontmatter** (maschinenlesbar) + lesbarer Markdown-Body (Kurzbeschreibung, Inhalte, Qualifikationsziele/Kompetenzen, Lehrformen, Literatur). Wichtige Frontmatter-Felder: `modulcode`, `titel_de`/`titel_en`, `modultyp`, `studiensemester`, `fachrichtungen` (Vertiefung), `crp`, Aufwand (`arbeitsaufwand_h`/`praesenzzeit_h`/`selbststudium_h`), `sprache`, `haeufigkeit`, `pruefungsleistungen`, `lehrveranstaltungsart`, `sws{}`, `modulverantwortliche`, `lehrende`.

---

## Vertiefungsrichtungen

Der Studiengang bietet drei Vertiefungsrichtungen. Das Grundstudium ist weitgehend identisch; ab dem **3./4. Semester** gibt es **vertiefungsspezifische Pflichtmodule**, im **5. Semester** werden Wahlpflichtmodule belegt. In den Tabellen kennzeichnet die Spalte **Vertiefung**, für welche Richtung ein Modul gilt (`alle` = für alle drei verpflichtend).

- **Data Science** · **IT-Security** · **Softwareentwicklung**

---

## Studienverlauf nach Semester

| Sem. | Code | Modul | CrP | Vertiefung | Typ |
| :--: | :--: | --- | :--: | --- | --- |
| 1. | 1002 | [Datenmodellierung und Datenmanagement](./module/1002-datenmodellierung-und-datenmanagement.md) | 5 | alle | Pflicht |
| 1. | 1003 | [Einführung in die Programmierung](./module/1003-einfuehrung-in-die-programmierung.md) | 5 | alle | Pflicht |
| 1. | 1004 | [Grundlagen der Informatik 1](./module/1004-grundlagen-der-informatik-1.md) | 5 | alle | Pflicht |
| 1. | 1005 | [Mathematik für Informatiker 1](./module/1005-mathematik-fuer-informatiker-1.md) | 5 | alle | Pflicht |
| 1. | 3001 | [Rechnerarchitekturen und Betriebssysteme](./module/3001-rechnerarchitekturen-und-betriebssysteme.md) | 6 | alle | Pflicht |
| 1. + 2 | 80001/80002 | [Coaching-Selbstkompetenz](./module/80001-80002-coaching-selbstkompetenz.md) | 4 | alle | Pflicht |
| 1./2 | 1100 | [Praxisphase 1](./module/1100-praxisphase-1.md) | 3 | alle | Pflicht |
| 2. | 2001 | [Algorithmen und Datenstrukturen](./module/2001-algorithmen-und-datenstrukturen.md) | 5 | alle | Pflicht |
| 2. | 2002 | [Datenbanksysteme](./module/2002-datenbanksysteme.md) | 5 | alle | Pflicht |
| 2. | 2004 | [Grundlagen der Informatik 2](./module/2004-grundlagen-der-informatik-2.md) | 6 | alle | Pflicht |
| 2. | 2005 | [Mathematik für Informatiker 2](./module/2005-mathematik-fuer-informatiker-2.md) | 6 | alle | Pflicht |
| 2. | 8001 | [Sozialkompetenz](./module/8001-sozialkompetenz.md) | 4 | alle | Pflicht |
| 2./3 | 2000 | [Praxisphase 2](./module/2000-praxisphase-2.md) | 3 | alle | Pflicht |
| 3. | 1006 | [Grundlagen der Informationssicherheit](./module/1006-grundlagen-der-informationssicherheit.md) | 5 | alle | Pflicht |
| 3. | 3002 | [Requirements Engineering](./module/3002-requirements-engineering.md) | 6 | alle | Pflicht |
| 3. | 3003 | [Software Engineering](./module/3003-software-engineering.md) | 6 | alle | Pflicht |
| 3. | 3005 | [Statistische Grundlagen des Machine Learning](./module/3005-statistische-grundlagen-des-machine-learning.md) | 5 | Data Science | Pflicht |
| 3. | 3006 | [Management der Informationssicherheit: Standards und Normen](./module/3006-management-der-informationssicherheit-standards-und-normen.md) | 5 | IT-Security | Pflicht |
| 3. | 3007 | [Entwicklung grafischer Bedieneroberflächen und User-Interface-Design](./module/3007-entwicklung-grafischer-bedieneroberflaechen-und-user-interface-d.md) | 5 | Softwareentwicklung | Pflicht |
| 3. | 8002 | [Betriebsethik](./module/8002-betriebsethik.md) | 4 | alle | Pflicht |
| 3./4 | 3000 | [Praxisphase 3](./module/3000-praxisphase-3.md) | 4 | alle | Pflicht |
| 4. | 4001 | [Mobile Technologien](./module/4001-mobile-technologien.md) | 6 | Softwareentwicklung | Pflicht |
| 4. | 4002 | [Modellgetriebene Softwareentwicklung](./module/4002-modellgetriebene-softwareentwicklung.md) | 6 | Softwareentwicklung | Pflicht |
| 4. | 4003 | [Softwarearchitekturen](./module/4003-softwarearchitekturen.md) | 6 | alle | Pflicht |
| 4. | 4004 | [Softwarequalität](./module/4004-softwarequalitaet.md) | 6 | alle | Pflicht |
| 4. | 4005 | [Big Data und Data Wrangling](./module/4005-big-data-und-data-wrangling.md) | 6 | Data Science | Pflicht |
| 4. | 4006 | [Machine Learning](./module/4006-machine-learning.md) | 6 | Data Science | Pflicht |
| 4. | 4007 | [Secure Coding](./module/4007-secure-coding.md) | 6 | IT-Security | Pflicht |
| 4. | 4008 | [Penetration Testing](./module/4008-penetration-testing.md) | 6 | IT-Security | Pflicht |
| 4. | 8004 | [Projektmanagement](./module/8004-projektmanagement.md) | 5 | alle | Pflicht |
| 5. | 5010 | [Betriebliche Standardsoftware](./module/5010-betriebliche-standardsoftware.md) | 5 | Softwareentwicklung | Wahlpflicht |
| 5. | 5011 | [Data Warehousing und Business Intelligence](./module/5011-data-warehousing-und-business-intelligence.md) | 5 | Data Science | Wahlpflicht |
| 5. | 5013 | [Geschäftsprozessmanagement](./module/5013-geschaeftsprozessmanagement.md) | 5 | IT-Security, Softwareentwicklung | Wahlpflicht |
| 5. | 5014 | [Intelligente Prozesse, Maschinen und Produkte](./module/5014-intelligente-prozesse-maschinen-und-produkte.md) | 5 | Data Science, Softwareentwicklung | Wahlpflicht |
| 5. | 5015 | [Predictive Analytics](./module/5015-predictive-analytics.md) | 5 | alle | Wahlpflicht |
| 5. | 5016 | [Funktionale Programmierung](./module/5016-funktionale-programmierung.md) | 5 | alle | Wahlpflicht |
| 5. | 5017 | [Web Technologies](./module/5017-web-technologies.md) | 5 | IT-Security, Softwareentwicklung | Wahlpflicht |
| 5. | 5018 | [Programming Paradigms](./module/5018-programming-paradigms.md) | 5 | alle | Wahlpflicht |
| 5. | 5019 | [Wissensbasierte Methoden](./module/5019-wissensbasierte-methoden.md) | 5 | alle | Wahlpflicht |
| 5. | 5020 | [Kommerzielle Standardsoftware](./module/5020-kommerzielle-standardsoftware.md) | 5 | alle | Wahlpflicht |
| 5. | 5024 | [Programmierung mit ABAP-Objects von SAP](./module/5024-programmierung-mit-abap-objects-von-sap.md) | 5 | Softwareentwicklung | Wahlpflicht |
| 6. | 6000 | [Projektstudium](./module/6000-projektstudium.md) | 32 | alle | Pflicht |
| 7. | 7001 | [Case Studies: aktuelle und zukunftsweisende Anwendungen](./module/7001-case-studies-aktuelle-und-zukunftsweisende-anwendungen.md) | 6 | alle | Pflicht |
| 7. | 7004 | [Industrielle Simulation](./module/7004-industrielle-simulation.md) | 6 | alle | Pflicht |
| 7. | 7010 | [Bachelor-Thesis](./module/7010-bachelor-thesis.md) | 12 | alle | Pflicht |
| 7. | 7011 | [Bachelor-Kolloquium](./module/7011-bachelor-kolloquium.md) | 3 | alle | Pflicht |
| 7. | NEU | [Rechtliche Aspekte der Informationstechnologie](./module/NEU-rechtliche-aspekte-der-informationstechnologie.md) | 5 | alle | Pflicht |

> Ein Studienpfad umfasst alle `alle`-Pflichtmodule **plus** die Pflichtmodule **einer** Vertiefungsrichtung **plus** die im 5. Semester gewählten Wahlpflichtmodule — zusammen **210 CrP**. Praxisphasen (1–3), Projektstudium (6. Sem.) und Bachelor-Thesis + Kolloquium (7. Sem.) sind für alle verpflichtend.

---

## Vertiefungsspezifische Pflichtmodule (3.–4. Semester)

**Data Science**

| Code | Modul | Sem. | CrP |
| :--: | --- | :--: | :--: |
| 3005 | [Statistische Grundlagen des Machine Learning](./module/3005-statistische-grundlagen-des-machine-learning.md) | 3. | 5 |
| 4005 | [Big Data und Data Wrangling](./module/4005-big-data-und-data-wrangling.md) | 4. | 6 |
| 4006 | [Machine Learning](./module/4006-machine-learning.md) | 4. | 6 |

**IT-Security**

| Code | Modul | Sem. | CrP |
| :--: | --- | :--: | :--: |
| 3006 | [Management der Informationssicherheit: Standards und Normen](./module/3006-management-der-informationssicherheit-standards-und-normen.md) | 3. | 5 |
| 4007 | [Secure Coding](./module/4007-secure-coding.md) | 4. | 6 |
| 4008 | [Penetration Testing](./module/4008-penetration-testing.md) | 4. | 6 |

**Softwareentwicklung**

| Code | Modul | Sem. | CrP |
| :--: | --- | :--: | :--: |
| 3007 | [Entwicklung grafischer Bedieneroberflächen und User-Interface-Design](./module/3007-entwicklung-grafischer-bedieneroberflaechen-und-user-interface-d.md) | 3. | 5 |
| 4001 | [Mobile Technologien](./module/4001-mobile-technologien.md) | 4. | 6 |
| 4002 | [Modellgetriebene Softwareentwicklung](./module/4002-modellgetriebene-softwareentwicklung.md) | 4. | 6 |

---

## Wahlpflichtmodule (5. Semester)

Im 5. Semester werden Wahlpflichtmodule (je 5 CrP) belegt. Die Spalte **Vertiefung** zeigt die Zuordnung laut Modulhandbuch (`alle` = für alle Richtungen wählbar).

| Code | Modul | CrP | Vertiefung | Modulverantwortliche |
| :--: | --- | :--: | --- | --- |
| 5010 | [Betriebliche Standardsoftware](./module/5010-betriebliche-standardsoftware.md) | 5 | Softwareentwicklung | Prof. Dr. Michael Guckert |
| 5011 | [Data Warehousing und Business Intelligence](./module/5011-data-warehousing-und-business-intelligence.md) | 5 | Data Science | Prof. Dr. Harald Ritz |
| 5013 | [Geschäftsprozessmanagement](./module/5013-geschaeftsprozessmanagement.md) | 5 | IT-Security, Softwareentwicklung | Prof. Dr. Peter Hohmann |
| 5014 | [Intelligente Prozesse, Maschinen und Produkte](./module/5014-intelligente-prozesse-maschinen-und-produkte.md) | 5 | Data Science, Softwareentwicklung | Prof. Dr. Michael Guckert |
| 5015 | [Predictive Analytics](./module/5015-predictive-analytics.md) | 5 | alle | Prof. Dr. Michael Guckert |
| 5016 | [Funktionale Programmierung](./module/5016-funktionale-programmierung.md) | 5 | alle | Prof. Dr. Guckert |
| 5017 | [Web Technologies](./module/5017-web-technologies.md) | 5 | IT-Security, Softwareentwicklung | Prof. Dr. Michael Guckert |
| 5018 | [Programming Paradigms](./module/5018-programming-paradigms.md) | 5 | alle | Prof. Dr. Michael Guckert |
| 5019 | [Wissensbasierte Methoden](./module/5019-wissensbasierte-methoden.md) | 5 | alle | Prof. Dr. Michael Guckert |
| 5020 | [Kommerzielle Standardsoftware](./module/5020-kommerzielle-standardsoftware.md) | 5 | alle | Prof. Dr. Peter Hohmann |
| 5024 | [Programmierung mit ABAP-Objects von SAP](./module/5024-programmierung-mit-abap-objects-von-sap.md) | 5 | Softwareentwicklung | Prof. Dr. Peter Hohmann |

---

## Hinweise zur Datenqualität

Inhalte wurden möglichst wortgetreu übernommen; offensichtliche OCR-/Trennungsfehler wurden behutsam korrigiert, inhaltliche Eigenheiten des Originals blieben erhalten. Besonderheiten:

- **Ankreuzfelder aus Seitenbildern:** In diesem PDF sind die Checkbox-Zeichen (☒/☐) nicht im Textextrakt enthalten. `fachrichtungen`, `sprache`, `dauer_semester`, `haeufigkeit`, `bonuspunkte` und die angekreuzte `lehrveranstaltungsart` wurden daher aus den gerenderten Seitenbildern gelesen. ([Issue #8](https://github.com/carstenlucke/studplus_mhb_po/issues/8))
- **Vertiefungsspezifische Pflichtmodule:** Nicht alle Pflichtmodule gelten für alle Vertiefungen (z. B. *Entwicklung grafischer Bedieneroberflächen* (3007) nur Softwareentwicklung; *Statistische Grundlagen des Machine Learning* (3005) nur Data Science; *Management der Informationssicherheit* (3006) nur IT-Security).
- **Modulcode "NEU":** Das Modul *Rechtliche Aspekte der Informationstechnologie* trägt im PDF wörtlich den Code „NEU" (noch kein finaler Modulcode vergeben). ([Issue #3](https://github.com/carstenlucke/studplus_mhb_po/issues/3))
- **Doppelcode 80001/80002:** *Coaching-Selbstkompetenz* wird über das 1. + 2. Semester geführt (zwei Teilcodes, eine Modulbeschreibung).
- **Schreibvariante:** Der Studiengang heißt im PDF teils „Softwaretechnik" statt „Softwaretechnologie"; maßgeblich ist „Softwaretechnologie (B.Sc.)". ([Issue #6](https://github.com/carstenlucke/studplus_mhb_po/issues/6))
- **Abweichende Prüfungsformen:** Einige Module weichen ab (z. B. *Case Studies* (7001) und *Projektstudium* (6000) mit „Anwesenheit"/unbenotet); siehe jeweilige Moduldatei.
- **Vollständigkeit (47 Module):** 6 Module mit eingerückter `Modulcode`-Zeile wurden bei der Extraktion zunächst übersehen und nachträglich ergänzt — alle 47 sind vorhanden und validiert ([Issue #7](https://github.com/carstenlucke/studplus_mhb_po/issues/7)).
- **Web-Angaben** (Modulnamen, SWS, CP auf der Studiengangsseite) dienen nur der Orientierung; maßgeblich sind die Werte aus dem Modulhandbuch.

---

_Stand der Aufbereitung: 27.06.2026 · 47 Modulbeschreibungen · Quelle: Modulhandbuch Version 4 (Fassung 11.12.2024)._
