---
name: journal-task-triage
description: Findet alle offenen Tasks ≥ 7 Kalendertage über die letzten Daily Notes und erzwingt pro Task eine aktive Entscheidung. Verwende bei Backlog-Stau, vor Wochenreview oder wenn `journal-daily-finish-off` wegen Backlog-Limit abbricht.
---

Triage offener Tasks, die zu lange mitwandern. Verhindert, dass Punkte stillschweigend zwischen Daily Notes weitergeschleppt werden, ohne dass eine Entscheidung getroffen wurde.

## Schritte

1. **Datumsbereich bestimmen:** Heute ist `{{date}}`. Lies die letzten 14 Tagesnotizen aus `01-daily/YYYY/MM/YYYY-MM-DD.md` (auch über Monatsgrenzen).

2. **Offene Tasks sammeln:** Aus der aktuellen Daily Note und den letzten Notizen alle offenen `- [ ]` Tasks extrahieren.

3. **Aging bestimmen:**
   - Primärquelle ist die `(seit DD.MM.)` oder `(seit DD.MM.YYYY)` Markierung am Task.
   - Falls fehlend: erstes Auftreten in den letzten 14 Daily Notes als Erstdatum verwenden.
   - **Schwelle:** Tasks mit Alter ≥ 7 Kalendertage sind triage-pflichtig.

4. **Pro triage-pflichtigem Task aktive Entscheidung einfordern.** Nicht stillschweigend übernehmen. Bernhard wählt eine der vier Optionen:
   - **Tun** → konkreten Slot setzen (heute oder morgen, Zeitfenster)
   - **Verschieben** → konkretes Datum oder Kalender-Eintrag (Datum, Dauer, Titel)
   - **Archivieren** → in passende Kontextdatei (Projekt/Area) als Kontext oder ins Archiv; Task verschwindet aus Daily-Loop
   - **Delegieren** → an wen, mit Übergabe-Hinweis

5. **Entscheidungen umsetzen:**
   - Tun: Task in der aktuellen Daily Note unter `## Heute` mit Slot-Hinweis platzieren.
   - Verschieben: Task aus aktueller Daily Note entfernen; in Ziel-Daily-Note einfügen oder als Kalender-Eintrag (`create_event` über Calendar-MCP) anlegen, Task verlinkt den Termin.
   - Archivieren: Inhalt in passende Projekt-/Area-Datei verdichten; Task aus Daily Note streichen.
   - Delegieren: Task umformulieren auf Übergabe-Punkt (z.B. „warten auf Antwort von X bis Datum"); aus eigenen offenen Tasks entfernen.

6. **Ausgabe:** Kompakte Liste der getroffenen Entscheidungen, getrennt nach Kategorie. Kein neues Backlog erzeugen.

## Trigger

- Aufruf direkt: `/journal-task-triage`
- Pflichtschritt im Wochenreview, bevor `## Fokus nächste Woche` priorisiert wird.
- Fallback wenn `journal-daily-finish-off` wegen Backlog-Limit (>10 offene Tasks) abbricht.

## Regeln

- Keine Triage ohne explizite Entscheidung pro Task. Stillschweigendes Übernehmen ist genau das Problem, das dieser Skill verhindert.
- Verschiebungen, die im Wochenreview als „in Kalender heben" markiert wurden, werden hier verbindlich als Kalender-Eintrag umgesetzt.
- Archivieren ist eine legitime Entscheidung, kein Versagen — nicht jeder Task muss erledigt werden.
