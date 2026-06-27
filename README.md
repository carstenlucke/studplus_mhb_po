# StudiumPlus / THM – Modulhandbücher, strukturiert für KI-Agenten

Dieses Repository enthält **Modulhandbücher dualer Studiengänge** des Wissenschaftlichen Zentrums
Duales Hochschulstudium (ZDH) der **Technischen Hochschule Mittelhessen (THM)** / **StudiumPlus** –
aus den offiziellen PDF-Modulhandbüchern extrahiert und in ein einheitliches, maschinen- **und**
menschenlesbares Format überführt: **eine Markdown-Datei pro Modul** mit YAML-Frontmatter, plus je
Studiengang eine Index-`README.md`.

> Ziel: Modulinformationen so aufbereiten, dass ein KI-Agent sie zuverlässig durchsuchen, vergleichen
> und beantworten kann – bei voller Nachvollziehbarkeit zur Quelle.

## Studiengänge

| Studiengang | Abschluss | Module | Sem. | CrP | Fachrichtungen / Vertiefungen | Index |
| --- | --- | :--: | :--: | :--: | --- | --- |
| **Prozessmanagement** | M.Sc. | 23 | 3 | 90 | Steuerung von Geschäftsprozessen · Technische Prozesse | [→ Übersicht](./modulhandbuch-prozessmanagement/README.md) |
| **Betriebswirtschaft** | B.A. | 73 | 7 | ~210 | Mittelstandsmanagement · Logistikmanagement · Wirtschaftsinformatik · Krankenversicherungsmanagement | [→ Übersicht](./modulhandbuch-betriebswirtschaft/README.md) |
| **Softwaretechnologie** | B.Sc. | 47 | 7 | 210 | Data Science · IT-Security · Softwareentwicklung | [→ Übersicht](./modulhandbuch-softwaretechnologie/README.md) |

_Gesamt: **143 Modulbeschreibungen**. Quelle jeweils das offizielle Modulhandbuch (Stand 2024);
das Original-PDF liegt je Studiengang unter `quellen/`._

## Aufbau

```
modulhandbuch-<studiengang>/
├── README.md          # Index: Studiengangsüberblick, Verlaufspläne je Fachrichtung, Links
├── module/            # je Modul eine Datei  <modulcode>-<slug>.md
└── quellen/           # Original-Modulhandbuch (PDF) als Rohmaterial
```

Jede Modul-Datei hat denselben Aufbau: **YAML-Frontmatter** (maschinenlesbar) gefolgt von einem
lesbaren Markdown-Body.

```yaml
---
modulcode: "1003"
titel_de: "Controlling"
titel_en: "Controlling"
modultyp: "Pflichtmodul"          # oder "Wahlpflichtmodul"
studiensemester: 1
fachrichtungen: ["…"]             # Vertiefung(en), in denen das Modul gilt
crp: 5
arbeitsaufwand_h: 125
praesenzzeit_h: 50
selbststudium_h: 75
sprache: "Deutsch"
pruefungsleistungen: "Klausur (90 Minuten)"
modulverantwortliche: "…"
# … Voraussetzungen, Bonuspunkte, Lehrform, sws{}, Lehrende
---
```

Der Body enthält: Kurzbeschreibung (DE/EN), Inhalte, Qualifikationsziele &
Kompetenzen (Fach-/Methoden-/Sozial-/Selbstkompetenzen), Lehr-/Lernformen, Literatur sowie eine
Quellenangabe mit Modulcode und Seitenzahl im PDF.

## Wie das Repo erstellt wird

Die Extraktion ist als wiederverwendbares Verfahren dokumentiert:

- **[`CLAUDE.md`](./CLAUDE.md)** – Playbook mit dem verbindlichen Vorgehen (PDF → Text/Seitenbilder →
  Modul-Split → Workflow-Orchestrierung → Index → Validierung), der Modul-Vorlage und den bekannten
  Stolperfallen.
- **[`.claude/commands/extract.md`](./.claude/commands/extract.md)** – Slash-Command
  `/extract <pdf> [website]` (für [Claude Code](https://claude.com/claude-code)), der ein weiteres
  Modulhandbuch konform aufbereitet.

Die Inhalte werden möglichst wortgetreu übernommen; Ankreuzfelder werden – je nach PDF – aus dem
Text oder aus gerenderten Seitenbildern gelesen. Jede Modul-Datei wird gegen ein festes Schema
validiert; CrP-Summen werden je Fachrichtung plausibilisiert. Strukturrelevante Auffälligkeiten sind
im jeweiligen Studiengangs-`README.md` unter „Hinweise zur Datenqualität" dokumentiert.

## Quellen & Hinweise

Die Modulhandbücher und Studienverlaufspläne sind offizielle, öffentlich zugängliche Dokumente der
THM / StudiumPlus (siehe [studiumplus.de](https://studiumplus.de) bzw.
[thm.de](https://www.thm.de)). Maßgeblich für verbindliche Auskünfte sind stets die offiziellen
Originaldokumente und die jeweils gültige Prüfungsordnung; diese Aufbereitung dient der besseren
Durch- und Auffindbarkeit, ersetzt sie aber nicht.
