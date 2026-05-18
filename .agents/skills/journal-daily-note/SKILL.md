---
name: journal-daily-note
description: Legacy-Einstieg für Daily-Workflows. Verwende bevorzugt `journal-daily-preparation` oder `journal-daily-finish-off`.
---

Dieser Skill ist ein Einstiegspunkt aus Kompatibilitätsgründen.

## Routing

Das Routing ist deterministisch — keine Rückfrage an den Nutzer, einfach ausführen:

1. Wenn es um Tagesvorbereitung, Priorisierung oder Tagesnotiz für heute geht: nutze `journal-daily-preparation`.
2. Wenn es um Tagesabschluss, Review und Planung des nächsten Arbeitstags geht: nutze `journal-daily-finish-off`.
3. Wenn der Einstieg über `journal-daily-note` selbst kommt (z.B. Tagesroutine), gilt nach Uhrzeit:
   - vor `13:00`: `journal-daily-preparation` ausführen.
   - ab `13:00`: zuerst `journal-daily-finish-off`, danach `journal-daily-preparation` für den nächsten Arbeitstag.

"Interaktive Ausführung" bedeutet: Rückfragen innerhalb der Sub-Skills (z.B. Priorisierung, Entscheidungen) — nicht Rückfragen zum Routing selbst.
