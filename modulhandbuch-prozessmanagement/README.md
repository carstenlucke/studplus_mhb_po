# Modulhandbuch – Masterstudiengang Prozessmanagement (M.Sc.)

Strukturierte Aufbereitung aller Module des dualen Masterstudiengangs **Prozessmanagement
(Abschluss „Master of Science")** des Wissenschaftlichen Zentrums Duales Hochschulstudium (ZDH)
der **Technischen Hochschule Mittelhessen (THM)** / **StudiumPlus**.

- **Abschluss:** Master of Science (M.Sc.)
- **Regelstudienzeit:** 3 Semester (dual, berufsintegrierend)
- **Umfang:** 90 CrP (ECTS), je 30 CrP pro Semester
- **Fachrichtungen:**
  1. **Steuerung von Geschäftsprozessen**
  2. **Technische Prozesse**

Der erste Studienabschnitt ist für beide Fachrichtungen weitgehend identisch; die
fachrichtungsspezifischen Module liegen im 2. und 3. Semester.

> **Quellen**
> - Modulhandbuch zur Prüfungsordnung des ZDH der THM für den dualen Masterstudiengang
>   Prozessmanagement, **Version 7**, Fassung vom **11. September 2024** (PDF, 58 Seiten) —
>   Originaldokument abgelegt unter
>   [`quellen/Modulhandbuch_Prozessmanagement_Master_V7_2024-09-11.pdf`](./quellen/Modulhandbuch_Prozessmanagement_Master_V7_2024-09-11.pdf).
> - Studiengangs-Webseiten StudiumPlus (Studienverlaufspläne je Fachrichtung), abgerufen 06/2026:
>   [Steuerung von Geschäftsprozessen](https://studiumplus.de/studiengaenge/prozessmanagement/prozessmanagement-steuerung-von-geschaeftsprozessen/) ·
>   [Technische Prozesse](https://studiumplus.de/studiengaenge/prozessmanagement/prozessmanagement-technische-prozesse/)

---

## Verwendung (für KI-Agenten & Menschen)

Jedes Modul liegt als eigene Markdown-Datei im Ordner [`module/`](./module/) und hat dieselbe
Struktur: ein **YAML-Frontmatter** mit maschinenlesbaren Feldern, gefolgt von einem lesbaren
Markdown-Body (Kurzbeschreibung, Inhalte, Qualifikationsziele/Kompetenzen, Lehrformen, Literatur).

Wichtigste Frontmatter-Felder:

| Feld | Bedeutung |
| --- | --- |
| `modulcode` | Modulnummer laut Modulhandbuch (Pflicht: 1xxx–3xxx, Wahlpflicht: 4xxx) |
| `titel_de` / `titel_en` | Modulbezeichnung deutsch / englisch |
| `modultyp` | `Pflichtmodul` oder `Wahlpflichtmodul` |
| `studiensemester` | Empfohlenes Fachsemester (1–3) |
| `fachrichtungen` | Fachrichtung(en), in denen das Modul belegt wird |
| `crp` | ECTS-Leistungspunkte (1 CrP = 25 h Arbeitsaufwand) |
| `arbeitsaufwand_h` / `praesenzzeit_h` / `selbststudium_h` | Aufwand in Stunden |
| `sprache`, `haeufigkeit`, `dauer_semester` | Unterrichtssprache, Turnus, Moduldauer |
| `pruefungsleistungen` / `pruefungsvorleistungen` | Prüfungsform(en) |
| `lehrveranstaltungsart`, `sws{}` | Art nach KapVO + SWS je Kategorie |
| `modulverantwortliche`, `lehrende` | Verantwortung / Lehrende |

---

## Studienverlaufsplan je Fachrichtung

Pro Semester werden 30 CrP erworben (gesamt 90 CrP). „Wahlpflichtfach 1" im 2. Semester wird durch
**eines** der neun Wahlpflichtmodule (siehe unten) belegt.

### Fachrichtung: Steuerung von Geschäftsprozessen

| Sem. | Modul | Code | CrP | Typ |
| :--: | --- | :--: | :--: | --- |
| 1 | [Grundlagen des Prozessmanagements](./module/1002-grundlagen-prozessmanagement.md) | 1002 | 5 | Pflicht |
| 1 | [Controlling](./module/1003-controlling.md) | 1003 | 5 | Pflicht |
| 1 | [Innovations- und Changemanagement](./module/1004-innovations-changemanagement.md) | 1004 | 5 | Pflicht |
| 1 | [Human Resource Management](./module/1005-human-resource-management.md) | 1005 | 5 | Pflicht |
| 1 | [Projektphase 1](./module/1001-projektphase-1.md) | 1001 | 10 | Pflicht |
| | **Summe 1. Semester** | | **30** | |
| 2 | [Produktionsprozesse](./module/2002-produktionsprozesse.md) | 2002 | 5 | Pflicht |
| 2 | [Vertiefung des Prozessmanagements](./module/2004-vertiefung-prozessmanagement.md) | 2004 | 5 | Pflicht |
| 2 | [Internationales Marketing/-Vertrieb](./module/2003-internationales-marketing-vertrieb.md) | 2003 | 5 | Pflicht |
| 2 | Wahlpflichtfach 1 _(1 aus 9, siehe unten)_ | 4xxx | 5 | Wahlpflicht |
| 2 | [Projektphase 2](./module/2001-projektphase-2.md) | 2001 | 10 | Pflicht |
| | **Summe 2. Semester** | | **30** | |
| 3 | [Supply Chain Management](./module/3005-supply-chain-management.md) | 3005 | 5 | Pflicht |
| 3 | [Unternehmensplanung und Führungsprozesse](./module/3003-unternehmensplanung-fuehrungsprozesse.md) | 3003 | 5 | Pflicht |
| 3 | [Master-Thesis + Kolloquium](./module/3001-master-thesis-kolloquium.md) | 3001 | 20 | Pflicht |
| | **Summe 3. Semester** | | **30** | |
| | **Gesamt** | | **90** | |

### Fachrichtung: Technische Prozesse

| Sem. | Modul | Code | CrP | Typ |
| :--: | --- | :--: | :--: | --- |
| 1 | [Grundlagen des Prozessmanagements](./module/1002-grundlagen-prozessmanagement.md) | 1002 | 5 | Pflicht |
| 1 | [Controlling](./module/1003-controlling.md) | 1003 | 5 | Pflicht |
| 1 | [Innovations- und Changemanagement](./module/1004-innovations-changemanagement.md) | 1004 | 5 | Pflicht |
| 1 | [Human Resource Management](./module/1005-human-resource-management.md) | 1005 | 5 | Pflicht |
| 1 | [Projektphase 1](./module/1001-projektphase-1.md) | 1001 | 10 | Pflicht |
| | **Summe 1. Semester** | | **30** | |
| 2 | [Produktionsprozesse](./module/2002-produktionsprozesse.md) | 2002 | 5 | Pflicht |
| 2 | [Vertiefung des Prozessmanagements](./module/2004-vertiefung-prozessmanagement.md) | 2004 | 5 | Pflicht |
| 2 | [Optimierung komplexer Systeme unter Einsatz von MSR-Techniken](./module/2004-optimierung-komplexer-systeme-msr.md) | 2004 | 5 | Pflicht |
| 2 | Wahlpflichtfach 1 _(1 aus 9, siehe unten)_ | 4xxx | 5 | Wahlpflicht |
| 2 | [Projektphase 2](./module/2001-projektphase-2.md) | 2001 | 10 | Pflicht |
| | **Summe 2. Semester** | | **30** | |
| 3 | [Supply Chain Management](./module/3005-supply-chain-management.md) | 3005 | 5 | Pflicht |
| 3 | [Messtechnik und Sensorik in der industriellen Praxis](./module/3004-messtechnik-sensorik.md) | 3004 | 5 | Pflicht |
| 3 | [Master-Thesis + Kolloquium](./module/3001-master-thesis-kolloquium.md) | 3001 | 20 | Pflicht |
| | **Summe 3. Semester** | | **30** | |
| | **Gesamt** | | **90** | |

> **Unterschiede zwischen den Fachrichtungen:** Das 1. Semester ist identisch. Im 2. Semester
> ersetzt **Internationales Marketing/-Vertrieb** (Steuerung) bzw. **Optimierung komplexer Systeme
> unter Einsatz von MSR-Techniken** (Technische Prozesse) das jeweils fachrichtungsspezifische
> Modul; im 3. Semester **Unternehmensplanung und Führungsprozesse** (Steuerung) bzw.
> **Messtechnik und Sensorik in der industriellen Praxis** (Technische Prozesse).

---

## Pflichtmodule (Übersicht)

| Code | Modul | Sem. | CrP | Fachrichtung | Modulverantwortliche |
| :--: | --- | :--: | :--: | --- | --- |
| 1001 | [Projektphase 1](./module/1001-projektphase-1.md) | 1 | 10 | beide | Prof. Dr. Jens Minnert |
| 1002 | [Grundlagen des Prozessmanagements](./module/1002-grundlagen-prozessmanagement.md) | 1 | 5 | beide | Prof. Dr. Pia Robinson |
| 1003 | [Controlling](./module/1003-controlling.md) | 1 | 5 | beide | Prof. Dr. Pia Robinson |
| 1004 | [Innovations- und Changemanagement](./module/1004-innovations-changemanagement.md) | 1 | 5 | beide | Prof. Dr. Fabian Tjon |
| 1005 | [Human Resource Management](./module/1005-human-resource-management.md) | 1 | 5 | beide | Prof. Dr. Pia Robinson |
| 2001 | [Projektphase 2](./module/2001-projektphase-2.md) | 2 | 10 | beide | Prof. Dr. Jens Minnert |
| 2002 | [Produktionsprozesse](./module/2002-produktionsprozesse.md) | 2 | 5 | beide | Prof. Dr. Fabian Tjon |
| 2003 | [Internationales Marketing/-Vertrieb](./module/2003-internationales-marketing-vertrieb.md) | 2 | 5 | Steuerung von Geschäftsprozessen | Prof. Dr. Fabian Tjon |
| 2004 | [Vertiefung des Prozessmanagements](./module/2004-vertiefung-prozessmanagement.md) | 2 | 5 | beide | Prof. Dr. Pia Robinson |
| 2004 | [Optimierung komplexer Systeme unter Einsatz von MSR-Techniken](./module/2004-optimierung-komplexer-systeme-msr.md) | 2 | 5 | Technische Prozesse | Prof. Dr. Alfred Karbach |
| 3001 | [Master-Thesis + Kolloquium](./module/3001-master-thesis-kolloquium.md) | 3 | 20 | beide | Prof. Dr. Jens Minnert |
| 3003 | [Unternehmensplanung und Führungsprozesse](./module/3003-unternehmensplanung-fuehrungsprozesse.md) | 3 | 5 | Steuerung von Geschäftsprozessen | Prof. Dr. Pia Robinson |
| 3004 | [Messtechnik und Sensorik in der industriellen Praxis](./module/3004-messtechnik-sensorik.md) | 3 | 5 | Technische Prozesse | Prof. Dr. Eberhard Schultheiß |
| 3005 | [Supply Chain Management](./module/3005-supply-chain-management.md) | 3 | 5 | beide | Prof. Dr. Marcus Fuchs |

## Wahlpflichtmodule (Übersicht)

Aus den folgenden neun Modulen wird im 2. Semester **ein** Modul als „Wahlpflichtfach 1" (5 CrP)
gewählt. Sie stehen grundsätzlich für **beide Fachrichtungen** zur Wahl.

| Code | Modul | Sem. | CrP | Sprache | Modulverantwortliche |
| :--: | --- | :--: | :--: | --- | --- |
| 4002 | [Angewandte Wirtschaftspsychologie](./module/4002-angewandte-wirtschaftspsychologie.md) | 2 | 5 | Deutsch | Prof. Dr. Fabian Tjon |
| 4003 | [Existenzgründung](./module/4003-existenzgruendung.md) | 2 | 5 | Deutsch | Prof. Dr. Pia Robinson |
| 4004 | [Intercultural Communication and Negotiation](./module/4004-intercultural-communication-negotiation.md) | 2 | 5 | Englisch | Prof. Dr. Pia Robinson |
| 4007 | [IT-Management](./module/4007-it-management.md) | 2 | 5 | Deutsch | Prof. Dr. Fabian Tjon |
| 4008 | [Konsumgütervertrieb & Konsumentenverhalten](./module/4008-konsumguetervertrieb-konsumentenverhalten.md) | 2 | 5 | Deutsch | Prof. Dr. Pia Robinson |
| 4010 | [Social Media Strategie & Markenführung und -kommunikation](./module/4010-social-media-strategie-markenfuehrung.md) | 2 | 5 | Deutsch | Prof. Dr. Pia Robinson |
| 4011 | [Vertiefung Controlling](./module/4011-vertiefung-controlling.md) | 2 | 5 | Deutsch | Prof. Dr. Pia Robinson |
| 4020 | [Ethik und interkulturelle Kompetenz](./module/4020-ethik-interkulturelle-kompetenz.md) | 2 | 5 | Deutsch | Prof. Dr. Jens Minnert |
| 4021 | [Building Brands vom Startup bis zum Corporate](./module/4021-building-brands.md) | 2 | 5 | Deutsch | Prof. Dr. Pia Robinson |

---

## Hinweise zur Datenqualität

Die Modulinhalte wurden möglichst wortgetreu aus dem Modulhandbuch übernommen. Offensichtliche
OCR-/Silbentrennungsfehler wurden behutsam korrigiert; inhaltliche Eigenheiten des Originals
(inkl. Tippfehler im Quelltext) blieben erhalten. Strukturell relevante Punkte:

- **Doppelter Modulcode 2004:** Der Code `2004` ist im Modulhandbuch zweifach vergeben — für
  *Vertiefung des Prozessmanagements* **und** für *Optimierung komplexer Systeme unter Einsatz von
  MSR-Techniken*. In der Fachrichtung *Technische Prozesse* werden im 2. Semester laut Verlaufsplan
  **beide** Module geführt. Dies ist eine Inkonsistenz der Quelldokumentation; beide Module sind
  hier als getrennte Dateien abgebildet.
- **Projektphasen / Master-Thesis** sind „Coaching"/projektorientierte Module ohne Präsenz-SWS
  (Projektphase 1 & 2: je 10 CrP, 250 h; Master-Thesis + Kolloquium: 20 CrP, 500 h). Bei
  *Projektphase 2* ist im PDF keine Lehrveranstaltungsart nach KapVO angekreuzt.
- **Vertiefung Controlling (4011):** Im PDF sind sowohl „Seminar" als auch „Thesis" markiert;
  maßgeblich (SWS-tragend) ist Seminar (4 SWS) — das Thesis-Kreuz ist vermutlich ein
  versehentlicher Marker.
- **Ethik und interkulturelle Kompetenz (4020):** Als Prüfungsleistung ist ausschließlich
  „Anwesenheit (100 %)" angegeben.
- Die Webseite der Fachrichtung *Technische Prozesse* schreibt „Human **Ressource** Management";
  maßgeblich ist die Modulhandbuch-Schreibweise „Human Resource Management".

---

_Stand der Aufbereitung: 27.06.2026 · 23 Modulbeschreibungen · Quelle: Modulhandbuch Version 7
(Fassung 11.09.2024)._
