---
name: journal-daily-preparation
description: Bereitet einen Ziel-Arbeitstag im Journal vor. Verwende diesen Skill für Tagesvorbereitung, Tagesnotiz anlegen/aktualisieren oder Fokusplanung für einen konkreten Tag.
---

Bereite die Tagesnotiz für den Zieltag im Projektverzeichnis vor.

## Ablauf

1. **Zieltag bestimmen**
   - Falls ein konkreter Tag genannt ist: diesen als Zieltag verwenden.
   - Falls kein Tag genannt ist: von `{{date}}` ausgehen und den nächsten sinnvollen regulären Arbeitstag bestimmen.
   - Reguläre Arbeitstage sind Montag bis Freitag.
   - Feiertage und ganztägige eigene Abwesenheiten aus den Kalenderquellen nicht als Zieltag planen.
   - Teilweise Abwesenheiten und Team-Abwesenheiten als Planungskontext berücksichtigen, aber den Tag nicht automatisch überspringen.

2. **Tagesnotiz öffnen oder anlegen**
   - Notizpfad: `01-daily/YYYY/MM/YYYY-MM-DD.md`.
   - Falls vorhanden: aktualisieren, Struktur beibehalten.
   - Falls nicht vorhanden: exakt das Template aus `assets/template.md` verwenden.

3. **Planungskontext laden**
   - Vorherige relevante Daily Note lesen (letzter regulärer Arbeitstag).
   - Kontext aus `ABOUTME.md`, `03-projects/` und `04-areas/` berücksichtigen.

4. **Kalender für den Zieltag vorbereiten**
   - Kalenderdaten zuerst über `calendar-lookup` holen (vollständige Rohtermine).
   - Relevanzbewertung und Selektion erfolgt hier im Skill, nicht im `calendar-lookup`.
   - Kalenderquellen über `calendar-lookup` laden; maßgeblich ist `05-resources/calendars.md`, `declined` ignorieren.
   - Folgetag aus den `calendar-lookup`-Daten prüfen: Termine mit Vorbereitungsbedarf identifizieren und nötige Vorbereitungs-Tasks noch für den Zieltag in `## Heute` einplanen.
   - Wenn der Inhalt eines Termins aus dem Namen allein nicht klar erkennbar ist (z.B. Refinement, Retro, generischer Name): Links aus der Terminbeschreibung abrufen und lesen, um Themen oder Agenda in die Tagesübersicht einzufließen zu lassen.
   - Bei Retros mit Versionsnummer im Titel (z.B. „Retro TAO 12.12.1"): Jira-Query `project = <KEY> AND fixVersion = "<VERSION>"` ausführen und kompakten Überblick als Kontext zum Termin ergänzen — Bug-Anzahl, wichtigste Features/Stories, Anteil Dependency-Updates.
   - Signal vor Vollständigkeit:
     - Standardmäßig ausblenden: Standups, troii Kaffee, reine Routinetermine ohne Vorbereitungsbedarf
     - Immer zeigen: `Produkt Jour Fixe`, externe/entscheidungsrelevante Termine, Termine mit Vorbereitungsbedarf
   - Wenn ein gezeigter Termin Vorbereitung braucht: Vorbereitung als `- [ ]` in `## Heute` ergänzen.
     - **Nur eigene Vorbereitung eintragen.** Material- oder Artefakt-Status, der in der Verantwortung des Organisators liegt (z.B. „Miro-Stand prüfen" bei einer fremden Retro, Agenda-Befüllung), gehört nicht in Bernhards Tasks. Inhaltliche Eigenvorbereitung (Konzept lesen, eigene Punkte sammeln) gehört rein.

5. **Tasks einplanen**
   - `## Heute`: nach Projekt/Bereich gruppieren (nicht nach meldender Person).
   - Section-Namen orientieren sich an [05-resources/projects-and-repos.md](../../../05-resources/projects-and-repos.md). Sammelbezeichnungen (z.B. `tour`, `timr Backend`, `timr Mobile`) sind ok, wenn sie inhaltlich passen. **Jira-Keys bezeichnen aber genau eine Komponente** — `TOUR` = tour iOS, `TOURA` = tour Android, `TIMR` = timr Backend/Web etc. — und dürfen nicht als Sammelbezeichnung über andere Komponenten hinweg verwendet werden.
   - Übernommene Punkte mit `(seit DD.MM.YYYY)` markieren — Datum ist der Tag, an dem der Task erstmals als Task eingetragen wurde.
   - Neue Punkte ohne Zusatz.
   - Nur konkrete Aufgaben mit Tagesbezug eintragen. Beiläufige, unsortierte oder noch nicht terminierte Themen bleiben in `00-inbox/` bzw. werden mit `journal-inbox` erfasst.
   - Keine operativen Checkbox-Duplikate aus Projekt-, Area-, Meeting- oder People-Dateien übernehmen; stattdessen den konkreten nächsten Schritt für den Zieltag formulieren.

6. **Kompakte Ausgabe**
   - Geplante Schwerpunkte und signalstarke Termine kurz zusammenfassen.

## Konventionen

- Links zu Journal-Dateien relativ vom Speicherort der Daily Note
- Jira-Links als `https://troiisoftware.atlassian.net/browse/TIMR-XXXX`
