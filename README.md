# Journal-Scaffolding

Starter-Vault für ein persönliches Arbeits-Journal mit Claude als Co-Pilot.

Plain Markdown, durchsuchbar mit Standard-Werkzeugen, versioniert mit Git. Claude übernimmt die wiederkehrende Strukturarbeit (Tagesplanung, Inbox-Verarbeitung, Reviews, Querverweise) — entscheiden tust du selbst.

## Setup

1. **Diesen Ordner als eigenes Repo nutzen oder forken.** Pfad ist beliebig; üblich: `~/Developer/Journal` oder `~/Documents/Journal`.

2. **`ABOUTME.md` ausfüllen** — Kopie aus `ABOUTME.md.example` machen und an dich anpassen:

   ```bash
   cp ABOUTME.md.example ABOUTME.md
   ```

   Pflichtschritt — ohne ABOUTME.md weiß Claude nicht, was dein Kontext ist.

3. **AGENTS.md überfliegen** — die Konventionen (Sprache, Checkbox-Format, `**Entscheidung:**`) anpassen, falls du andere willst. Routing-Block bleibt meistens so.

4. **Claude Cowork öffnen** und dieses Verzeichnis als Projekt einbinden. AGENTS.md / CLAUDE.md werden automatisch geladen.

5. **Erste Tagesnotiz anlegen** — Skill triggern:

   > Bitte führe `journal-daily-preparation` aus.

   Claude liest deinen Kalender (falls verbunden), legt die Tagesnotiz unter `01-daily/YYYY/MM/YYYY-MM-DD.md` an und baut Tagesblöcke aus offenen Tasks und „Auf dem Radar"-Punkten.

6. **Automatisierungen aktivieren (empfohlen)** — siehe `05-resources/automations.md` für scheduled tasks (Tagesroutine, Wochenreview).

## Tägliche Routine

| Wann | Skill | Was passiert |
|---|---|---|
| Morgens | `journal-daily-preparation` | Tagesnotiz baut sich aus Kalender + offenen Tasks + Auf-dem-Radar |
| Abends | `journal-daily-finish-off` | Tagesabschluss — was erledigt, was bleibt, Übergabe an morgen |
| Vor Meeting | `journal-meeting-preparation` | Kalender + Kontextseite → Vorbereitungspunkte |
| Nach Meeting | `journal-meeting-note` | Strukturierte Meeting-Notiz |
| Freitag | `journal-weekly-review` | Reflexion (kein Backlog) |
| Monatsende | `journal-monthly-review` | Schritt zurück |

## Verzeichnis-Struktur

```
00-inbox/         – Schnelle Erfassungen ohne Tagesbezug
01-daily/         – Tagesnotizen (YYYY/MM/YYYY-MM-DD.md)
02-meetings/      – Meeting-Notizen
03-projects/      – Projekte mit Ziel und Deadline
04-areas/         – Laufende Verantwortungsbereiche
05-resources/     – Referenzmaterial + Templates
06-reviews/       – Wochen- und Monatsreviews
99-archive/       – Abgeschlossenes
.agents/skills/   – Eingearbeitete Routinen (SKILL.md)
```

Frontmatter, Konventionen, Routing-Tabelle: siehe [AGENTS.md](AGENTS.md).

## Templates

Vorlagen für neue Dateien liegen unter `05-resources/templates/`:

- `daily-template.md` — Tagesnotiz
- `meeting-template.md` — Meeting-Notiz
- `project-template.md` — Projekt-Kontextseite
- `weekly-review-template.md` — Wochenreview

Die Skills nutzen sie automatisch, du kannst sie aber auch direkt kopieren.

## Pflege

- **Wöchentlich:** `journal-weekly-review` jeden Freitag — Reflexion, nicht Backlog
- **Monatlich:** `journal-monthly-review` Schritt zurück
- **Bei Korrekturen:** nicht den Einzelfall fixen — das Muster im passenden Skill nachziehen. Details siehe AGENTS.md.

## Lizenz / Nutzung

Dieses Scaffolding ist als Starter gedacht. Forke es, passe es an, mach es deins. Skills sind bewusst klein gehalten — schreib eigene, sobald du den Stil verinnerlicht hast.
