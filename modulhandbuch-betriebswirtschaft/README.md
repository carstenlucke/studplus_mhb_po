# Modulhandbuch – Dualer Bachelorstudiengang Betriebswirtschaft (B.A.)

Strukturierte Aufbereitung aller Module des **dualen Bachelorstudiengangs Betriebswirtschaft**
(Abschluss „Bachelor of Arts") des Wissenschaftlichen Zentrums Duales Hochschulstudium (ZDH)
der **Technischen Hochschule Mittelhessen (THM)** / **StudiumPlus**.

- **Abschluss:** Bachelor of Arts (B.A.)
- **Regelstudienzeit:** 7 Semester (dual, berufsintegrierend; Studienbeginn zum Wintersemester)
- **Umfang:** ca. **210 CrP** (ECTS) – je Fachrichtung **185 CrP Pflichtmodule** + Wahlpflichtbereich (5. Semester)
- **Fachrichtungen (Vertiefungen):**
  1. **Mittelstandsmanagement**
  2. **Logistikmanagement**
  3. **Wirtschaftsinformatik**
  4. **Krankenversicherungsmanagement**

Die Semester 1–3 sind weitgehend gemeinsam (mit fachrichtungsspezifischen Einzelmodulen); die
Vertiefung liegt v.a. in den Semestern 4, 5 und 7. Das 6. Semester ist durchgängig das
**Projektstudium im Unternehmen**.

> **Quellen**
> - Modulhandbuch (Modulbeschreibungen zur Prüfungsordnung des ZDH der THM) für den dualen
>   Bachelorstudiengang Betriebswirtschaft, **Version 4**, Fassung vom **11. Dezember 2024**
>   (PDF, 160 Seiten, 73 Module) — Originaldokument abgelegt unter
>   [`quellen/Modulhandbuch_Betriebswirtschaft_V4_2024-12-11.pdf`](./quellen/Modulhandbuch_Betriebswirtschaft_V4_2024-12-11.pdf).
> - Studiengangs-Webseiten StudiumPlus (Studienverlaufspläne je Fachrichtung), abgerufen 06/2026:
>   [Mittelstandsmanagement](https://studiumplus.de/studiengaenge/betriebswirtschaft/betriebswirtschaft-mittelstandsmanagement/) ·
>   [Logistikmanagement](https://studiumplus.de/studiengaenge/betriebswirtschaft/betriebswirtschaft-logistikmanagement/) ·
>   [Wirtschaftsinformatik](https://studiumplus.de/studiengaenge/betriebswirtschaft/betriebswirtschaft-wirtschaftsinformatik/) ·
>   [Krankenversicherungsmanagement](https://studiumplus.de/studiengaenge/betriebswirtschaft/betriebswirtschaft-krankenversicherungsmanagement/)

---

## Verwendung (für KI-Agenten & Menschen)

Jedes Modul liegt als eigene Markdown-Datei im Ordner [`module/`](./module/) und hat dieselbe
Struktur: ein **YAML-Frontmatter** mit maschinenlesbaren Feldern, gefolgt von einem lesbaren
Markdown-Body (Kurzbeschreibung, Inhalte, Qualifikationsziele/Kompetenzen, Lehrformen, Literatur).

Wichtigste Frontmatter-Felder:

| Feld | Bedeutung |
| --- | --- |
| `modulcode` | Modulnummer laut Modulhandbuch |
| `titel_de` / `titel_en` | Modulbezeichnung deutsch / englisch |
| `modultyp` | `Pflichtmodul` oder `Wahlpflichtmodul` |
| `studiensemester` | Empfohlenes (erstes) Fachsemester (1–7) |
| `fachrichtungen` | Fachrichtung(en), in denen das Modul belegt wird (laut Ankreuzfeld) |
| `crp` | ECTS-Leistungspunkte (1 CrP = 25 h Arbeitsaufwand) |
| `arbeitsaufwand_h` / `praesenzzeit_h` / `selbststudium_h` | Aufwand in Stunden |
| `sprache`, `haeufigkeit`, `dauer_semester` | Unterrichtssprache, Turnus, Moduldauer |
| `pruefungsleistungen` / `pruefungsvorleistungen` | Prüfungsform(en) |
| `lehrveranstaltungsart`, `sws{}` | Art nach KapVO + SWS je Kategorie |
| `modulverantwortliche`, `lehrende` | Verantwortung / Lehrende |

> **Hinweis zur Quelle:** Im Quell-PDF sind Pflicht/Wahlpflicht, Fachrichtung, Sprache, Dauer,
> Häufigkeit, Bonuspunkte und Lehrveranstaltungsart als **Ankreuzfelder** kodiert. Diese
> Checkbox-Zustände erscheinen in der reinen Textextraktion **nicht** und wurden daher aus den
> **Seitenbildern** des PDF gelesen (siehe „Hinweise zur Datenqualität").

---

## Studienverlaufsplan je Fachrichtung

Aufgeführt sind die **Pflichtmodule** je Semester (Quelle: Ankreuzfeld „Verwendbarkeit" im PDF).
Im **5. Semester** liegt der **Wahlpflichtbereich**: Es werden Wahlpflichtmodule (i.d.R. 5 Module
à 5 CrP) bis zum Erreichen von 210 CrP gewählt (Liste siehe unten). Das **6. Semester** ist das
Projektstudium im Unternehmen (32 CrP).

### Fachrichtung: Mittelstandsmanagement

| Sem. | Modul | Code | CrP | Typ |
| :--: | --- | :--: | :--: | --- |
| 1 | [Grundlagen der BWL](./module/1001-grundlagen-der-bwl.md) | 1001 | 5 | Pflicht |
| 1 | [Mathematik für Betriebswirte](./module/1002-mathematik-fuer-betriebswirte.md) | 1002 | 5 | Pflicht |
| 1 | [Wirtschaftsinformatik 1: Werkzeuge und Systeme der Bürokommunikation](./module/1004-wirtschaftsinformatik-1-werkzeuge-und-systeme-der-buerokommunikation.md) | 1004 | 5 | Pflicht |
| 1 | [Recht 1: BGB und HGB](./module/1006-recht-1-bgb-und-hgb.md) | 1006 | 5 | Pflicht |
| 1 | [Praxisphase 1](./module/1100-praxisphase-1.md) | 1100 | 3 | Pflicht |
| 1 | [Coaching-Selbstkompetenz](./module/80001-80002-coaching-selbstkompetenz.md) | 80001/80002 | 4 | Pflicht |
| 1 | [Personal / Organisation](./module/8005-personal-organisation.md) | 8005 | 5 | Pflicht |
| | **Summe 1. Semester** | | **32** | |
| 2 | [Praxisphase 2](./module/2000-praxisphase-2.md) | 2000 | 3 | Pflicht |
| 2 | [Externes Rechnungswesen](./module/2001-externes-rechnungswesen.md) | 2001 | 5 | Pflicht |
| 2 | [Statistik](./module/2002-statistik.md) | 2002 | 5 | Pflicht |
| 2 | [Recht 2: Arbeitsrecht](./module/2006-recht-2-arbeitsrecht.md) | 2006 | 5 | Pflicht |
| 2 | [Betriebsethik](./module/8002-betriebsethik.md) | 8002 | 4 | Pflicht |
| 2 | [VWL](./module/8006-vwl.md) | 8006 | 5 | Pflicht |
| | **Summe 2. Semester** | | **27** | |
| 3 | [Praxisphase 3](./module/3000-praxisphase-3.md) | 3000 | 4 | Pflicht |
| 3 | [Internes Rechnungswesen](./module/3001-internes-rechnungswesen.md) | 3001 | 5 | Pflicht |
| 3 | [Finanzierung / Steuern](./module/3002-finanzierung-steuern.md) | 3002 | 5 | Pflicht |
| 3 | [Wirtschaftsinformatik 2: Inner- und zwischenbetriebliches Informationsmanagement](./module/3005-wirtschaftsinformatik-2-inner-und-zwischenbetriebliches-informationsmanagement.md) | 3005 | 5 | Pflicht |
| 3 | [Marketing](./module/8007-marketing.md) | 8007 | 5 | Pflicht |
| 3 | [Unternehmensführung und Steuerung](./module/8008-unternehmensfuehrung-und-steuerung.md) | 8008 | 5 | Pflicht |
| | **Summe 3. Semester** | | **29** | |
| 4 | [Vertrieb](./module/4003-vertrieb.md) | 4003 | 5 | Pflicht |
| 4 | [Betriebliche Standardsoftware](./module/4004-betriebliche-standardsoftware.md) | 4004 | 5 | Pflicht |
| 4 | [Materialwirtschaft / Produktion](./module/4005-materialwirtschaft-produktion.md) | 4005 | 5 | Pflicht |
| 4 | [Strategisches und operatives Controlling](./module/4006-strategisches-und-operatives-controlling.md) | 4006 | 5 | Pflicht |
| 4 | [Sozialkompetenz](./module/8001-sozialkompetenz.md) | 8001 | 4 | Pflicht |
| 4 | [Projektmanagement](./module/8004-projektmanagement.md) | 8004 | 5 | Pflicht |
| 4 | [Business English](./module/8009-business-english.md) | 8009 | 6 | Pflicht |
| | **Summe 4. Semester** | | **35** | |
| 5 | Wahlpflichtbereich _(i.d.R. 5 Module à 5 CrP, siehe unten)_ | – | 25 | Wahlpflicht |
| | **Summe 5. Semester** | | **25** | |
| 6 | [Projektstudium](./module/6000-projektstudium.md) | 6000 | 32 | Pflicht |
| | **Summe 6. Semester** | | **32** | |
| 7 | [Bilanz- und Steuerpolitik](./module/7001-bilanz-und-steuerpolitik.md) | 7001 | 5 | Pflicht |
| 7 | [Nachhaltigkeit und Gesellschaftliche Verantwortung](./module/7004-nachhaltigkeit-und-gesellschaftliche-verantwortung.md) | 7004 | 5 | Pflicht |
| 7 | [Bachelor-Thesis](./module/7010-bachelor-thesis.md) | 7010 | 12 | Pflicht |
| 7 | [Bachelor-Kolloquium](./module/7011-bachelor-kolloquium.md) | 7011 | 3 | Pflicht |
| 7 | [Businessplan](./module/7202-businessplan.md) | 7202 | 5 | Pflicht |
| | **Summe 7. Semester** | | **30** | |
| | **Pflichtmodule gesamt** | | **185** | |
| | **inkl. Wahlpflichtbereich (Ziel)** | | **210** | |

### Fachrichtung: Logistikmanagement

| Sem. | Modul | Code | CrP | Typ |
| :--: | --- | :--: | :--: | --- |
| 1 | [Grundlagen der BWL](./module/1001-grundlagen-der-bwl.md) | 1001 | 5 | Pflicht |
| 1 | [Mathematik für Betriebswirte](./module/1002-mathematik-fuer-betriebswirte.md) | 1002 | 5 | Pflicht |
| 1 | [Wirtschaftsinformatik 1: Werkzeuge und Systeme der Bürokommunikation](./module/1004-wirtschaftsinformatik-1-werkzeuge-und-systeme-der-buerokommunikation.md) | 1004 | 5 | Pflicht |
| 1 | [Praxisphase 1](./module/1100-praxisphase-1.md) | 1100 | 3 | Pflicht |
| 1 | [Interlogistik](./module/1401-interlogistik.md) | 1401 | 5 | Pflicht |
| 1 | [Coaching-Selbstkompetenz](./module/80001-80002-coaching-selbstkompetenz.md) | 80001/80002 | 4 | Pflicht |
| 1 | [Personal / Organisation](./module/8005-personal-organisation.md) | 8005 | 5 | Pflicht |
| | **Summe 1. Semester** | | **32** | |
| 2 | [Praxisphase 2](./module/2000-praxisphase-2.md) | 2000 | 3 | Pflicht |
| 2 | [Externes Rechnungswesen](./module/2001-externes-rechnungswesen.md) | 2001 | 5 | Pflicht |
| 2 | [Statistik](./module/2002-statistik.md) | 2002 | 5 | Pflicht |
| 2 | [Logistikkonzepte](./module/2401-logistikkonzepte.md) | 2401 | 5 | Pflicht |
| 2 | [Betriebsethik](./module/8002-betriebsethik.md) | 8002 | 4 | Pflicht |
| 2 | [VWL](./module/8006-vwl.md) | 8006 | 5 | Pflicht |
| | **Summe 2. Semester** | | **27** | |
| 3 | [Praxisphase 3](./module/3000-praxisphase-3.md) | 3000 | 4 | Pflicht |
| 3 | [Internes Rechnungswesen](./module/3001-internes-rechnungswesen.md) | 3001 | 5 | Pflicht |
| 3 | [Finanzierung / Steuern](./module/3002-finanzierung-steuern.md) | 3002 | 5 | Pflicht |
| 3 | [Wirtschaftsinformatik 2: Inner- und zwischenbetriebliches Informationsmanagement](./module/3005-wirtschaftsinformatik-2-inner-und-zwischenbetriebliches-informationsmanagement.md) | 3005 | 5 | Pflicht |
| 3 | [Marketing](./module/8007-marketing.md) | 8007 | 5 | Pflicht |
| 3 | [Unternehmensführung und Steuerung](./module/8008-unternehmensfuehrung-und-steuerung.md) | 8008 | 5 | Pflicht |
| | **Summe 3. Semester** | | **29** | |
| 4 | [Strategisches und operatives Controlling](./module/4006-strategisches-und-operatives-controlling.md) | 4006 | 5 | Pflicht |
| 4 | [Beschaffungs- und Produktionslogistik](./module/4401-beschaffungs-und-produktionslogistik.md) | 4401 | 5 | Pflicht |
| 4 | [Distributionslogistik](./module/4402-distributionslogistik.md) | 4402 | 5 | Pflicht |
| 4 | [Informationslogistik](./module/4403-informationslogistik.md) | 4403 | 5 | Pflicht |
| 4 | [Sozialkompetenz](./module/8001-sozialkompetenz.md) | 8001 | 4 | Pflicht |
| 4 | [Projektmanagement](./module/8004-projektmanagement.md) | 8004 | 5 | Pflicht |
| 4 | [Business English](./module/8009-business-english.md) | 8009 | 6 | Pflicht |
| | **Summe 4. Semester** | | **35** | |
| 5 | Wahlpflichtbereich _(i.d.R. 5 Module à 5 CrP, siehe unten)_ | – | 25 | Wahlpflicht |
| | **Summe 5. Semester** | | **25** | |
| 6 | [Projektstudium](./module/6000-projektstudium.md) | 6000 | 32 | Pflicht |
| | **Summe 6. Semester** | | **32** | |
| 7 | [Bachelor-Thesis](./module/7010-bachelor-thesis.md) | 7010 | 12 | Pflicht |
| 7 | [Bachelor-Kolloquium](./module/7011-bachelor-kolloquium.md) | 7011 | 3 | Pflicht |
| 7 | [Geschäftsprozesse](./module/7401-geschaeftsprozesse.md) | 7401 | 5 | Pflicht |
| 7 | [Recht für Logistiker](./module/7402-recht-fuer-logistiker.md) | 7402 | 5 | Pflicht |
| 7 | [Planspiel](./module/7403-planspiel.md) | 7403 | 5 | Pflicht |
| | **Summe 7. Semester** | | **30** | |
| | **Pflichtmodule gesamt** | | **185** | |
| | **inkl. Wahlpflichtbereich (Ziel)** | | **210** | |

### Fachrichtung: Wirtschaftsinformatik

| Sem. | Modul | Code | CrP | Typ |
| :--: | --- | :--: | :--: | --- |
| 1 | [Grundlagen der BWL](./module/1001-grundlagen-der-bwl.md) | 1001 | 5 | Pflicht |
| 1 | [Mathematik für Betriebswirte](./module/1002-mathematik-fuer-betriebswirte.md) | 1002 | 5 | Pflicht |
| 1 | [Wirtschaftsinformatik 1: Werkzeuge und Systeme der Bürokommunikation](./module/1004-wirtschaftsinformatik-1-werkzeuge-und-systeme-der-buerokommunikation.md) | 1004 | 5 | Pflicht |
| 1 | [Praxisphase 1](./module/1100-praxisphase-1.md) | 1100 | 3 | Pflicht |
| 1 | [Einführung in die Programmierung](./module/1501-einfuehrung-in-die-programmierung.md) | 1501 | 5 | Pflicht |
| 1 | [Coaching-Selbstkompetenz](./module/80001-80002-coaching-selbstkompetenz.md) | 80001/80002 | 4 | Pflicht |
| 1 | [Personal / Organisation](./module/8005-personal-organisation.md) | 8005 | 5 | Pflicht |
| | **Summe 1. Semester** | | **32** | |
| 2 | [Praxisphase 2](./module/2000-praxisphase-2.md) | 2000 | 3 | Pflicht |
| 2 | [Externes Rechnungswesen](./module/2001-externes-rechnungswesen.md) | 2001 | 5 | Pflicht |
| 2 | [Statistik](./module/2002-statistik.md) | 2002 | 5 | Pflicht |
| 2 | [Datenmodellierung und Datenmanagement](./module/2501-datenmodellierung-und-datenmanagement.md) | 2501 | 5 | Pflicht |
| 2 | [Softwareergonomie und grafische Benutzeroberflächen](./module/2502-softwareergonomie-und-grafische-benutzeroberflaechen.md) | 2502 | 5 | Pflicht |
| 2 | [Betriebsethik](./module/8002-betriebsethik.md) | 8002 | 4 | Pflicht |
| 2 | [VWL](./module/8006-vwl.md) | 8006 | 5 | Pflicht |
| | **Summe 2. Semester** | | **32** | |
| 3 | [Praxisphase 3](./module/3000-praxisphase-3.md) | 3000 | 4 | Pflicht |
| 3 | [Internes Rechnungswesen](./module/3001-internes-rechnungswesen.md) | 3001 | 5 | Pflicht |
| 3 | [Finanzierung / Steuern](./module/3002-finanzierung-steuern.md) | 3002 | 5 | Pflicht |
| 3 | [Wirtschaftsinformatik 2: Inner- und zwischenbetriebliches Informationsmanagement](./module/3005-wirtschaftsinformatik-2-inner-und-zwischenbetriebliches-informationsmanagement.md) | 3005 | 5 | Pflicht |
| 3 | [Marketing](./module/8007-marketing.md) | 8007 | 5 | Pflicht |
| 3 | [Unternehmensführung und Steuerung](./module/8008-unternehmensfuehrung-und-steuerung.md) | 8008 | 5 | Pflicht |
| | **Summe 3. Semester** | | **29** | |
| 4 | [Vertrieb](./module/4003-vertrieb.md) | 4003 | 5 | Pflicht |
| 4 | [Betriebliche Standardsoftware](./module/4004-betriebliche-standardsoftware.md) | 4004 | 5 | Pflicht |
| 4 | [Materialwirtschaft / Produktion](./module/4005-materialwirtschaft-produktion.md) | 4005 | 5 | Pflicht |
| 4 | [Strategisches und operatives Controlling](./module/4006-strategisches-und-operatives-controlling.md) | 4006 | 5 | Pflicht |
| 4 | [Sozialkompetenz](./module/8001-sozialkompetenz.md) | 8001 | 4 | Pflicht |
| 4 | [Projektmanagement](./module/8004-projektmanagement.md) | 8004 | 5 | Pflicht |
| 4 | [Business English](./module/8009-business-english.md) | 8009 | 6 | Pflicht |
| | **Summe 4. Semester** | | **35** | |
| 5 | Wahlpflichtbereich _(i.d.R. 5 Module à 5 CrP, siehe unten)_ | – | 25 | Wahlpflicht |
| | **Summe 5. Semester** | | **25** | |
| 6 | [Projektstudium](./module/6000-projektstudium.md) | 6000 | 32 | Pflicht |
| | **Summe 6. Semester** | | **32** | |
| 7 | [Bachelor-Thesis](./module/7010-bachelor-thesis.md) | 7010 | 12 | Pflicht |
| 7 | [Bachelor-Kolloquium](./module/7011-bachelor-kolloquium.md) | 7011 | 3 | Pflicht |
| 7 | [Recht für Wirtschaftsinformatiker](./module/7502-recht-fuer-wirtschaftsinformatiker.md) | 7502 | 5 | Pflicht |
| 7 | [Data Warehousing und Business Intelligence](./module/7901-data-warehousing-und-business-intelligence.md) | 7901 | 5 | Pflicht |
| | **Summe 7. Semester** | | **25** | |
| | **Pflichtmodule gesamt** | | **185** | |
| | **inkl. Wahlpflichtbereich (Ziel)** | | **210** | |

### Fachrichtung: Krankenversicherungsmanagement

| Sem. | Modul | Code | CrP | Typ |
| :--: | --- | :--: | :--: | --- |
| 1 | [Grundlagen der BWL](./module/1001-grundlagen-der-bwl.md) | 1001 | 5 | Pflicht |
| 1 | [Mathematik für Betriebswirte](./module/1002-mathematik-fuer-betriebswirte.md) | 1002 | 5 | Pflicht |
| 1 | [Wirtschaftsinformatik 1: Werkzeuge und Systeme der Bürokommunikation](./module/1004-wirtschaftsinformatik-1-werkzeuge-und-systeme-der-buerokommunikation.md) | 1004 | 5 | Pflicht |
| 1 | [Recht 1: BGB und HGB](./module/1006-recht-1-bgb-und-hgb.md) | 1006 | 5 | Pflicht |
| 1 | [Praxisphase 1](./module/1100-praxisphase-1.md) | 1100 | 3 | Pflicht |
| 1 | [Coaching-Selbstkompetenz](./module/80001-80002-coaching-selbstkompetenz.md) | 80001/80002 | 4 | Pflicht |
| 1 | [Personal / Organisation](./module/8005-personal-organisation.md) | 8005 | 5 | Pflicht |
| | **Summe 1. Semester** | | **32** | |
| 2 | [Praxisphase 2](./module/2000-praxisphase-2.md) | 2000 | 3 | Pflicht |
| 2 | [Externes Rechnungswesen](./module/2001-externes-rechnungswesen.md) | 2001 | 5 | Pflicht |
| 2 | [Statistik](./module/2002-statistik.md) | 2002 | 5 | Pflicht |
| 2 | [Recht 2: Arbeitsrecht](./module/2006-recht-2-arbeitsrecht.md) | 2006 | 5 | Pflicht |
| 2 | [Betriebsethik](./module/8002-betriebsethik.md) | 8002 | 4 | Pflicht |
| 2 | [VWL](./module/8006-vwl.md) | 8006 | 5 | Pflicht |
| | **Summe 2. Semester** | | **27** | |
| 3 | [Praxisphase 3](./module/3000-praxisphase-3.md) | 3000 | 4 | Pflicht |
| 3 | [Internes Rechnungswesen](./module/3001-internes-rechnungswesen.md) | 3001 | 5 | Pflicht |
| 3 | [Finanzierung / Steuern](./module/3002-finanzierung-steuern.md) | 3002 | 5 | Pflicht |
| 3 | [Wirtschaftsinformatik 2: Inner- und zwischenbetriebliches Informationsmanagement](./module/3005-wirtschaftsinformatik-2-inner-und-zwischenbetriebliches-informationsmanagement.md) | 3005 | 5 | Pflicht |
| 3 | [Marketing](./module/8007-marketing.md) | 8007 | 5 | Pflicht |
| 3 | [Unternehmensführung und Steuerung](./module/8008-unternehmensfuehrung-und-steuerung.md) | 8008 | 5 | Pflicht |
| | **Summe 3. Semester** | | **29** | |
| 4 | [Wirtschaftliches Gesundheitswesen 1: Kranken- und Pflegeversicherungen](./module/4302-wirtschaftliches-gesundheitswesen-1-kranken-und-pflegeversicherungen.md) | 4302 | 5 | Pflicht |
| 4 | [Versicherungs-, Beitrags- und Leistungswesen](./module/4303-versicherungs-beitrags-und-leistungswesen.md) | 4303 | 5 | Pflicht |
| 4 | [Marketing der Krankenversicherung](./module/6306-marketing-der-krankenversicherung.md) | 6306 | 5 | Pflicht |
| 4 | [Sozialkompetenz](./module/8001-sozialkompetenz.md) | 8001 | 4 | Pflicht |
| 4 | [Projektmanagement](./module/8004-projektmanagement.md) | 8004 | 5 | Pflicht |
| 4 | [Business English](./module/8009-business-english.md) | 8009 | 6 | Pflicht |
| | **Summe 4. Semester** | | **30** | |
| 5 | [Wirtschaftliches Gesundheitswesen 2: Krankenhausfinanzierung und -controlling](./module/5302-wirtschaftliches-gesundheitswesen-2-krankenhausfinanzierung-und-controlling.md) | 5302 | 5 | Pflicht |
| 5 | Wahlpflichtbereich _(Wahlpflichtmodule, siehe unten; teils höherwertig, z.B. 5031 = 10 CrP)_ | – | 25 | Wahlpflicht |
| | **Summe 5. Semester** | | **30** | |
| 6 | [Projektstudium](./module/6000-projektstudium.md) | 6000 | 32 | Pflicht |
| | **Summe 6. Semester** | | **32** | |
| 7 | [Verwaltungsverfahren, Schadenersatz, Organisation](./module/7005-verwaltungsverfahren-schadenersatz-organisation.md) | 7005 | 5 | Pflicht |
| 7 | [Bachelor-Thesis](./module/7010-bachelor-thesis.md) | 7010 | 12 | Pflicht |
| 7 | [Bachelor-Kolloquium](./module/7011-bachelor-kolloquium.md) | 7011 | 3 | Pflicht |
| 7 | [Controlling Krankenversicherungsmanagement](./module/7302-controlling-krankenversicherungsmanagement.md) | 7302 | 5 | Pflicht |
| 7 | [Spezielles Rechnungswesen der Krankenversicherungen](./module/7303-spezielles-rechnungswesen-der-krankenversicherungen.md) | 7303 | 5 | Pflicht |
| | **Summe 7. Semester** | | **30** | |
| | **Pflichtmodule gesamt** | | **185** | |
| | **inkl. Wahlpflichtbereich (Ziel)** | | **210** | |

> **Lesehinweis:** Die Semester-Summen folgen den CrP der einzelnen Pflichtmodule laut PDF;
> da Module wie *Coaching-Selbstkompetenz* (über 1./2. Sem.) und die *Praxisphasen* studienorganisatorisch
> über Semestergrenzen laufen, ergeben sich nicht überall exakt 30 CrP je Semester. Maßgeblich ist die
> **Gesamtsumme von 210 CrP** (185 CrP Pflicht + Wahlpflichtbereich) je Fachrichtung.

---

## Pflichtmodule (Übersicht)

52 Pflichtmodule. „Fachrichtung = alle" bedeutet: in allen vier Vertiefungen Pflicht.

| Code | Modul | Sem. | CrP | Fachrichtung | Modulverantwortliche |
| :--: | --- | :--: | :--: | --- | --- |
| 1001 | [Grundlagen der BWL](./module/1001-grundlagen-der-bwl.md) | 1 | 5 | alle | Prof. Dr. Pia Robinson |
| 1002 | [Mathematik für Betriebswirte](./module/1002-mathematik-fuer-betriebswirte.md) | 1 | 5 | alle | Prof. Dr. Michael Guckert |
| 1004 | [Wirtschaftsinformatik 1: Werkzeuge und Systeme der Bürokommunikation](./module/1004-wirtschaftsinformatik-1-werkzeuge-und-systeme-der-buerokommunikation.md) | 1 | 5 | alle | Prof. Dr. Michael Guckert |
| 1006 | [Recht 1: BGB und HGB](./module/1006-recht-1-bgb-und-hgb.md) | 1 | 5 | Mittelstand, Krankenvers. | Prof. Dr. Harald Danne |
| 1100 | [Praxisphase 1](./module/1100-praxisphase-1.md) | 1 | 3 | alle | Prof. Dr. Jens Minnert |
| 1401 | [Interlogistik](./module/1401-interlogistik.md) | 1 | 5 | Logistik | Prof. Dr. Fabian Tjon |
| 1501 | [Einführung in die Programmierung](./module/1501-einfuehrung-in-die-programmierung.md) | 1 | 5 | Wirtsch.-Inf. | Prof. Dr. Michael Guckert |
| 80001/80002 | [Coaching-Selbstkompetenz](./module/80001-80002-coaching-selbstkompetenz.md) | 1 | 4 | alle | Prof. Dr. Harald Danne |
| 8005 | [Personal / Organisation](./module/8005-personal-organisation.md) | 1 | 5 | alle | Prof. Dr. Fabian Tjon |
| 2000 | [Praxisphase 2](./module/2000-praxisphase-2.md) | 2 | 3 | alle | Prof. Dr. Jens Minnert |
| 2001 | [Externes Rechnungswesen](./module/2001-externes-rechnungswesen.md) | 2 | 5 | alle | Prof. Dr. Pia Robinson |
| 2002 | [Statistik](./module/2002-statistik.md) | 2 | 5 | alle | Prof. Dr. Michael Guckert |
| 2006 | [Recht 2: Arbeitsrecht](./module/2006-recht-2-arbeitsrecht.md) | 2 | 5 | Mittelstand, Krankenvers. | Prof. Dr. Harald Danne |
| 2401 | [Logistikkonzepte](./module/2401-logistikkonzepte.md) | 2 | 5 | Logistik | Prof. Dr. Fabian Tjon |
| 2501 | [Datenmodellierung und Datenmanagement](./module/2501-datenmodellierung-und-datenmanagement.md) | 2 | 5 | Wirtsch.-Inf. | Prof. Dr. Michael Guckert |
| 2502 | [Softwareergonomie und grafische Benutzeroberflächen](./module/2502-softwareergonomie-und-grafische-benutzeroberflaechen.md) | 2 | 5 | Wirtsch.-Inf. | Prof. Dr. Peter Edelmann |
| 8002 | [Betriebsethik](./module/8002-betriebsethik.md) | 2 | 4 | alle | Prof. Dr. Jens Minnert |
| 8006 | [VWL](./module/8006-vwl.md) | 2 | 5 | alle | Prof. Dr. Fabian Tjon |
| 3000 | [Praxisphase 3](./module/3000-praxisphase-3.md) | 3 | 4 | alle | Prof. Dr. Jens Minnert |
| 3001 | [Internes Rechnungswesen](./module/3001-internes-rechnungswesen.md) | 3 | 5 | alle | Prof. Dr. Pia Robinson |
| 3002 | [Finanzierung / Steuern](./module/3002-finanzierung-steuern.md) | 3 | 5 | alle | Prof. Dr. Pia Robinson |
| 3005 | [Wirtschaftsinformatik 2: Inner- und zwischenbetriebliches Informationsmanagement](./module/3005-wirtschaftsinformatik-2-inner-und-zwischenbetriebliches-informationsmanagement.md) | 3 | 5 | alle | Prof. Dr. Michael Guckert |
| 8007 | [Marketing](./module/8007-marketing.md) | 3 | 5 | alle | Prof. Dr. Pia Robinson |
| 8008 | [Unternehmensführung und Steuerung](./module/8008-unternehmensfuehrung-und-steuerung.md) | 3 | 5 | alle | Prof. Dr. Pia Robinson |
| 4003 | [Vertrieb](./module/4003-vertrieb.md) | 4 | 5 | Mittelstand, Wirtsch.-Inf. | Prof. Dr. Pia Robinson |
| 4004 | [Betriebliche Standardsoftware](./module/4004-betriebliche-standardsoftware.md) | 4 | 5 | Mittelstand, Wirtsch.-Inf. | Prof. Dr. Michael Guckert |
| 4005 | [Materialwirtschaft / Produktion](./module/4005-materialwirtschaft-produktion.md) | 4 | 5 | Mittelstand, Wirtsch.-Inf. | Prof. Dr. Fabian Tjon |
| 4006 | [Strategisches und operatives Controlling](./module/4006-strategisches-und-operatives-controlling.md) | 4 | 5 | Mittelstand, Logistik, Wirtsch.-Inf. | Prof. Dr. Pia Robinson |
| 4302 | [Wirtschaftliches Gesundheitswesen 1: Kranken- und Pflegeversicherungen](./module/4302-wirtschaftliches-gesundheitswesen-1-kranken-und-pflegeversicherungen.md) | 4 | 5 | Krankenvers. | Prof. Dr. Henning Schneider |
| 4303 | [Versicherungs-, Beitrags- und Leistungswesen](./module/4303-versicherungs-beitrags-und-leistungswesen.md) | 4 | 5 | Krankenvers. | Alexandra Bolich |
| 4401 | [Beschaffungs- und Produktionslogistik](./module/4401-beschaffungs-und-produktionslogistik.md) | 4 | 5 | Logistik | Prof. Dr. Fabian Tjon |
| 4402 | [Distributionslogistik](./module/4402-distributionslogistik.md) | 4 | 5 | Logistik | Prof. Dr. Fabian Tjon |
| 4403 | [Informationslogistik](./module/4403-informationslogistik.md) | 4 | 5 | Logistik | Prof. Dr. Fabian Tjon |
| 6306 | [Marketing der Krankenversicherung](./module/6306-marketing-der-krankenversicherung.md) | 4 | 5 | Krankenvers. | Prof. Dr. Ulrich Vossebein |
| 8001 | [Sozialkompetenz](./module/8001-sozialkompetenz.md) | 4 | 4 | alle | Prof. Dr. Pia Robinson |
| 8004 | [Projektmanagement](./module/8004-projektmanagement.md) | 4 | 5 | alle | Prof. Dr. Jens Hoßfeld |
| 8009 | [Business English](./module/8009-business-english.md) | 4 | 6 | alle | Prof. Dr. Jens Hoßfeld |
| 5302 | [Wirtschaftliches Gesundheitswesen 2: Krankenhausfinanzierung und -controlling](./module/5302-wirtschaftliches-gesundheitswesen-2-krankenhausfinanzierung-und-controlling.md) | 5 | 5 | Krankenvers. | Prof. Dr. Henning Schneider |
| 6000 | [Projektstudium](./module/6000-projektstudium.md) | 6 | 32 | alle | Prof. Dr. Jens Minnert |
| 7001 | [Bilanz- und Steuerpolitik](./module/7001-bilanz-und-steuerpolitik.md) | 7 | 5 | Mittelstand | Prof. Dr. Pia Robinson |
| 7004 | [Nachhaltigkeit und Gesellschaftliche Verantwortung](./module/7004-nachhaltigkeit-und-gesellschaftliche-verantwortung.md) | 7 | 5 | Mittelstand | Prof. Dr. Pia Robinson |
| 7005 | [Verwaltungsverfahren, Schadenersatz, Organisation](./module/7005-verwaltungsverfahren-schadenersatz-organisation.md) | 7 | 5 | Krankenvers. | Matthias Wörsdörfer |
| 7010 | [Bachelor-Thesis](./module/7010-bachelor-thesis.md) | 7 | 12 | alle | Prof. Dr. Jens Minnert |
| 7011 | [Bachelor-Kolloquium](./module/7011-bachelor-kolloquium.md) | 7 | 3 | alle | Prof. Dr. Jens Minnert |
| 7202 | [Businessplan](./module/7202-businessplan.md) | 7 | 5 | Mittelstand | Prof. Dr. Pia Robinson |
| 7302 | [Controlling Krankenversicherungsmanagement](./module/7302-controlling-krankenversicherungsmanagement.md) | 7 | 5 | Krankenvers. | Prof. Dr. Henning Schneider |
| 7303 | [Spezielles Rechnungswesen der Krankenversicherungen](./module/7303-spezielles-rechnungswesen-der-krankenversicherungen.md) | 7 | 5 | Krankenvers. | Prof. Dr. Pia Robinson |
| 7401 | [Geschäftsprozesse](./module/7401-geschaeftsprozesse.md) | 7 | 5 | Logistik | Prof. Dr. Peter Hohmann |
| 7402 | [Recht für Logistiker](./module/7402-recht-fuer-logistiker.md) | 7 | 5 | Logistik | Prof. Dr. Fabian Tjon |
| 7403 | [Planspiel](./module/7403-planspiel.md) | 7 | 5 | Logistik | Prof. Dr. Fabian Tjon |
| 7502 | [Recht für Wirtschaftsinformatiker](./module/7502-recht-fuer-wirtschaftsinformatiker.md) | 7 | 5 | Wirtsch.-Inf. | Prof. Dr. Harald Danne |
| 7901 | [Data Warehousing und Business Intelligence](./module/7901-data-warehousing-und-business-intelligence.md) | 7 | 5 | Wirtsch.-Inf. | Prof. Dr. Harald Ritz |

## Wahlpflichtmodule (Übersicht)

21 Wahlpflichtmodule im **5. Semester** (Wahlpflichtbereich). „Fachrichtung = alle"
bzw. „Wahlpflichtbereich" = grundsätzlich für alle Vertiefungen wählbar; eingeschränkte
Angaben entsprechen den im PDF angekreuzten Fachrichtungen.

| Code | Modul | CrP | Sprache | Fachrichtung (laut PDF) | Modulverantwortliche |
| :--: | --- | :--: | --- | --- | --- |
| 5014 | [Aktuelle Aspekte der Logistik](./module/5014-aktuelle-aspekte-der-logistik.md) | 5 | Deutsch | Logistik | Prof. Dr. Fabian Tjon |
| 5015 | [Aktuelle Themen im Marketing](./module/5015-aktuelle-themen-im-marketing.md) | 5 | Deutsch | alle | Prof. Dr. Fabian Tjon |
| 5016 | [Aktuelle Themen im Personal- und Organisationsmanagement](./module/5016-aktuelle-themen-im-personal-und-organisationsmanagement.md) | 5 | Deutsch | alle | Prof. Dr. Pia Robinson |
| 5019 | [Materialflussplanung](./module/5019-materialflussplanung.md) | 5 | Deutsch | Logistik | Prof. Dr. Fabian Tjon |
| 5022 | [Aktuelle Themen im Controlling](./module/5022-aktuelle-themen-im-controlling.md) | 5 | Deutsch | Wahlpflichtbereich | Prof. Dr. Fabian Tjon |
| 5023 | [Kostenmanagement](./module/5023-kostenmanagement.md) | 5 | Deutsch | alle | Prof. Dr. Fabian Tjon |
| 5026 | [Marktforschung](./module/5026-marktforschung.md) | 5 | Deutsch | alle | Prof. Dr. Fabian Tjon |
| 5027 | [Internationale Kapitalmärkte](./module/5027-internationale-kapitalmaerkte.md) | 5 | Deutsch | alle | Martin Jacobi |
| 5031 | [Schnittstellenmanagement und Projektierung](./module/5031-schnittstellenmanagement-und-projektierung.md) | 10 | Deutsch | Krankenvers. | Nina Kranz |
| 5038 | [Neue Business Modelle](./module/5038-neue-business-modelle.md) | 5 | Deutsch | Mittelstand, Logistik, Wirtsch.-Inf. | Prof. Dr. Fabian Tjon |
| 5047 | [Mitarbeitergewinnung, Mitarbeiterförderung und Mitarbeiterbindung](./module/5047-mitarbeitergewinnung-foerderung-bindung.md) | 5 | Deutsch | Mittelstand, Logistik, Wirtsch.-Inf. | Prof. Dr. Fabian Tjon |
| 7005 | [Intercultural Competence in English](./module/7005-intercultural-competence-in-english.md) | 5 | Englisch | Wahlpflichtbereich | Dr. Angelika Schlaefke |
| 7007 | [Investmanagement](./module/7007-investmanagement.md) | 5 | Deutsch | alle | Dr. Alexander Olten |
| 7012 | [Supply Chain Management](./module/7012-supply-chain-management.md) | 5 | Deutsch | Logistik | Prof. Dr. Fabian Tjon |
| 7018 | [e-Business / e-Commerce](./module/7018-e-business-e-commerce.md) | 5 | Deutsch | Wahlpflichtbereich | Prof. Dr. Michael Guckert |
| 7023 | [VWL 2](./module/7023-vwl-2.md) | 5 | Deutsch | alle | Prof. Dr. Markus Gerhard |
| 7037 | [Einführung in Operations Research mit Python](./module/7037-einfuehrung-in-operations-research-mit-python.md) | 5 | Deutsch | Wahlpflichtbereich | Prof. Dr. Pia Robinson |
| 7047 | [Personalentwicklung und -führung](./module/7047-personalentwicklung-und-fuehrung.md) | 5 | Deutsch | Mittelstand, Logistik, Wirtsch.-Inf. | Prof. Dr. Pia Robinson |
| 7068 | [Verhandlungsstrategien in Wirtschaft und Recht](./module/7068-verhandlungsstrategien-in-wirtschaft-und-recht.md) | 5 | Deutsch | alle | Prof. Dr. Fabian Tjon |
| 7085 | [Personalmanagement im Gesundheitswesen](./module/7085-personalmanagement-im-gesundheitswesen.md) | 5 | Deutsch | Krankenvers. | Prof. Dr. Henning Schneider |
| 8103 | [Unternehmensplanspiel](./module/8103-unternehmensplanspiel.md) | 5 | Deutsch | Mittelstand, Wirtsch.-Inf. | Prof. Dr. Fabian Tjon |

---

## Hinweise zur Datenqualität

Die Modulinhalte wurden möglichst **wortgetreu** aus dem Modulhandbuch übernommen. Offensichtliche
OCR-/Silbentrennungsfehler wurden behutsam korrigiert; inhaltliche Eigenheiten des Originals
(inkl. Tippfehler im Quelltext, z.B. „Rechtformwahl", „Ressource Planning", „Toyota Produktion
System") blieben erhalten. Strukturell relevante Punkte:

- **Ankreuzfelder nur im Seitenbild:** Das Quell-PDF kodiert die Checkboxen als Word-Formularfelder.
  Die reine Textextraktion (`pdftotext`) enthält **keine** `☒`/`☐`-Zeichen. Pflicht/Wahlpflicht und
  Studiensemester stehen als Klartext im Text; **Fachrichtung, Sprache, Dauer, Häufigkeit,
  Bonuspunkte** und die angekreuzte **Lehrveranstaltungsart** wurden aus den gerenderten
  Seitenbildern (150 dpi) gelesen. Die SWS-Zahlenwerte selbst stehen im Text.
- **Doppelter Modulcode 7005:** zweifach vergeben — für *Verwaltungsverfahren, Schadenersatz,
  Organisation* (Pflichtmodul, 7. Sem., Krankenversicherungsmanagement) **und** für *Intercultural
  Competence in English* (Wahlpflichtmodul, 5. Sem.). Beide sind als getrennte Dateien abgelegt
  (`7005-verwaltungsverfahren-…`, `7005-intercultural-competence-in-english`).
- **Sammel-/Doppelcode `80001/80002`:** Das Modul *Coaching-Selbstkompetenz* trägt im PDF den
  kombinierten Code `80001/80002` (4 CrP, läuft über 1.–2. Semester; auf den Fachrichtungs-Webseiten
  als „Coaching-Selbstkompetenz Teil 1/Teil 2" geführt). Dateiname: `80001-80002-coaching-selbstkompetenz.md`.
- **Modulcode im Text fehlend:** Beim Modul *Businessplan* fehlte der Code in der Textebene; aus dem
  Seitenbild als **7202** gelesen.
- **Wahlpflichtmodule ohne Fachrichtungs-Kreuz (5022, 7005, 7018, 7037):** In der „Verwendbarkeit"
  ist nur „Wahlpflichtmodul …" ohne Fachrichtungs-Ankreuzung gesetzt → für den gesamten
  Wahlpflichtbereich (alle Fachrichtungen) wählbar.
- **Abweichende CrP/Sonderformate:** *Projektstudium* (6000) = **32 CrP** (800 h, 6. Semester);
  *Bachelor-Thesis* (7010) = 12 CrP, *Bachelor-Kolloquium* (7011) = 3 CrP; *Praxisphasen 1–3*
  (1100/2000/3000) = je 3–4 CrP; *Coaching-Selbstkompetenz* = 4 CrP; *Schnittstellenmanagement und
  Projektierung* (5031, Wahlpflicht) = 10 CrP. Projektphasen/Thesis sind „Coaching"/projektorientiert,
  meist mit gebrochenen KapVO-SWS (z.B. Thesis 0,15 SWS, Seminar 0,33 SWS).
- **Mehrsemestrige Module:** Bei Modulen über mehrere Semester (z.B. Coaching 1./2., Praxisphasen,
  Blockmodule wie 4004/8009, „4. oder 5. Semester") ist `studiensemester` das **erste** Semester;
  die genaue Spanne steht im Body („**Semester:** …").
- **Web ↔ PDF:** Die Studienverlaufspläne der Webseiten bestätigen die Semesterlage und die
  fachrichtungsspezifischen Module. Abweichungen: Die Webseite **splittet** *Versicherungs-,
  Beitrags- und Leistungswesen* (4303) in „Versicherungs- & Beitragswesen" (Sem. 4) und
  „Leistungswesen" (Sem. 5); maßgeblich ist die **PDF-Schreibweise/Semesterlage** (ein Modul, 4. Sem.).
  Einzelne Modulnamen sind auf der Webseite abgekürzt (z.B. „Wirtschaftsinformatik 1" statt
  „Wirtschaftsinformatik 1: Werkzeuge und Systeme der Bürokommunikation").
- **CrP-Plausibilität:** Je Fachrichtung summieren sich die Pflichtmodule auf **185 CrP**; mit dem
  Wahlpflichtbereich des 5. Semesters wird die Zielsumme von **210 CrP** (7 × 30) erreicht. Die
  einzelnen Semestersummen weichen organisatorisch bedingt von 30 CrP ab (siehe Lesehinweis oben).

---

_Stand der Aufbereitung: 27.06.2026 · 73 Modulbeschreibungen · Quelle: Modulhandbuch
Betriebswirtschaft (B.A.), Version 4 (Fassung 11.12.2024)._
