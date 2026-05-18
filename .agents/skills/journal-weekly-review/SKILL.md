---
name: journal-weekly-review
description: Erstellt den Wochenreview aus Daily Notes, Kalender und Bereichs-/Projektkontext. Verwende diesen Skill für Wochenrückblick, Weekly Review oder Wochenzusammenfassung.
---

Erstelle einen Wochenreview für die aktuelle Woche im Journal-Vault.

## Schritte

1. **Kalenderwoche bestimmen:** Heute ist {{date}}. Bestimme Montag bis heute dieser Woche.

2. **Daily Notes lesen:** Bestimme den Datumsbereich Montag bis heute und lies alle vorhandenen Tagesnotizen für diese Tage in `01-daily/YYYY/MM/YYYY-MM-DD.md` (auch über Monatsgrenzen hinweg).

3. **Kalender der Woche:** Hole vergangene Termine der Woche aus Google Calendar.

4. **Extrahieren aus Daily Notes:**
   - Erledigte Aufgaben `- [x]`
   - Noch offene Aufgaben `- [ ]` als Reflexionsmaterial, nicht als neue Checkliste
   - Einträge unter `## Entscheidungen`
   - Einträge unter `## Tagesreflexion`

5. **Zusätzlichen Wochenkontext prüfen:**
   - `04-areas/`: relevante Fortschritte, offene Punkte und Auffälligkeiten der Woche
   - `03-projects/`: offene Initiativen mit Fortschritt oder dringenden Punkten
   - `00-inbox/`: unverarbeitete Notizen dieser Woche, auch Dateien ohne `status`

5a. **Projekt-/Area-Sweep:** `journal-context-sweep` aufrufen oder dessen Logik inline anwenden — alle aktiven Projekt- und Area-Seiten in `03-projects/` und `04-areas/` gegen die Daily Notes der Woche abgleichen. Pro Seite:
   - **Stand veraltet?** Update einpflegen (Verlauf-Eintrag mit Datum, Status/offene Fragen/nächste Schritte mitziehen), `letzter_sweep` aktualisieren.
   - **Keine Daily-Erwähnung in 14+ Tagen?** Bewusste Statusentscheidung treffen (`aktiv`, `wartend`, `pausiert`, `abgeschlossen`).
   - Querverweise auf umbenannte oder neue Projekt-/Area-Dateien korrigieren.

   **Keine Outcomes konstruieren:** Kalendertermine liefern Anlass und Kontext, aber kein Ergebnis. Entscheidungen, Zusagen, Bewertungen oder erledigte Fortschritte nur übernehmen, wenn sie in Daily Notes, Meeting Notes, Projekt- oder Area-Dateien dokumentiert sind. Fehlt ein erwartbares Ergebnis, im Review als offen oder nicht dokumentiert kennzeichnen.
   **Kein Backlog erzeugen:** Das Wochenreview ist Reflexion. Offene Punkte als Ursache, Kontext oder Muster beschreiben, nicht als Checkboxliste.
   **Inbox-Taktung:** Inbox-Reste kurz erwähnen. Wenn daraus konkrete Verarbeitung gewünscht ist, anschließend `journal-process-inbox` nutzen; nicht stillschweigend als Backlog ins Review übernehmen.

6. **Datei erstellen:** Unter `06-reviews/weekly/{{year}}-KW[xx].md` mit `assets/template.md`.

7. **Aging-Triage (Pflichtschritt):** Vor der Fokus-Priorisierung `journal-task-triage` aufrufen oder dessen Logik inline anwenden — alle offenen Tasks ≥ 7 Kalendertage müssen eine aktive Entscheidung erhalten (tun/verschieben/archivieren/delegieren). Nicht überspringen, auch wenn nichts auffällt.

8. **Fokus priorisieren:**
   - Schlage Top 3 Fokusthemen für nächste Woche vor, basierend auf Kalender und offenen Mustern.
   - Diese 3 Themen in `## Fokus nächste Woche` priorisiert eintragen.
   - Keine operative Checkboxliste erzeugen.
   - Decision-Log-Kandidaten markieren, aber nicht automatisch ins Decision Log duplizieren.

9. **Kalender-Aktionen:** Wenn der Review zu dem Schluss kommt, dass ein wiederkehrender Punkt „in Kalender gehoben" werden soll (statt täglich im Daily-Loop zu wandern), unter `## Kalender-Aktionen` konkrete Termin-Vorschläge ausgeben: Datum, Dauer, Titel. Diese Vorschläge sollen anschließend als Termine angelegt werden — die zugehörigen Tasks gehören danach nicht mehr in Daily Notes, sondern nur noch als Kalender-Eintrag.

10. **Bestätigung** + kompakte Zusammenfassung der Woche in 3-5 Sätzen.
