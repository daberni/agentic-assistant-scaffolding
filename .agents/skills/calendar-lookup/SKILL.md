---
name: calendar-lookup
description: Führt einen Kalender-Lookup über alle relevanten Kalender durch und liefert destillierte, aussagekräftige Terminlisten für einen Zeitraum.
---

Hole Kalenderinformationen für den gewünschten Zeitraum und liefere eine kompakte, aber aussagekräftige Terminliste.

Ziel: Nur die Informationen, die für Bewertung und Planung wirklich gebraucht werden — keine ETags, keine iCalUIDs, keine ConferenceData-Blöcke.

## Ablauf

1. **Zeitraum bestimmen**
   - Falls kein Zeitraum genannt ist: heute (`{{date}}`).
   - Mögliche Eingaben: heute, morgen, konkretes Datum, Datumsbereich.

2. **Zeitfenster-Strategie**
   - **Bis zu 3 Tage:** Eine Abfrage pro Kalender reicht.
   - **Mehr als 3 Tage (z.B. Wochensicht):** Wenn der `primary` viele Termine erwartet, lieber pro Tag parallel abfragen — spart Context und vermeidet Truncation.
   - Bei großen Rückgaben (File statt Inline-Ergebnis): immer sofort mit `jq` auf die relevanten Felder reduzieren, nicht das ganze File lesen.

3. **Kalenderquellen laden**
   - Verwende die Kalender-IDs aus `05-resources/calendars.md`.
   - Immer alle relevanten Kalender einbeziehen, nicht nur `primary`.
   - Alle Kalenderabfragen parallel schicken.
   - **Zeitfenster immer mindestens +1 Tag über den angefragten Zeitraum hinaus** abfragen, damit nachgelagerte Planungs-Skills Folgetermine bewerten können.

4. **Felder destillieren (Default)**
   Pro Termin nur folgende Felder behalten:
   - `summary` (Titel)
   - `start`, `end` (Uhrzeit oder Datum)
   - `location`
   - `responseStatus` (self)
   - `organizer` (E-Mail oder Name)
   - `htmlLink` — behalten, falls Referenz/Verlinkung nützlich ist
   - `recurringEventId` (nur als Flag, ob es ein wiederkehrender Termin ist)

   Weglassen: `etag`, `iCalUID`, `created`, `updated`, `sequence`, `kind`, `conferenceData`, `reminders`, `htmlLink`-Varianten, `hangoutLink`.

5. **Attendees intelligent behandeln**
   - **Default: Attendees weglassen bei wiederkehrenden Terminen** (`recurringEventId` ist gesetzt).
     - Einfaches, eindeutiges Kriterium — keine Titel-Heuristik nötig.
   - **Bei Einzelterminen: Attendees mitliefern** inkl. Name/E-Mail und `responseStatus` pro Person.
     - Das ist oft die wichtigste Information (wer ist dabei, wer hat zugesagt/abgesagt).
   - Auf expliziten Wunsch ("zeig mir auch die Teilnehmer der Standups") Attendees auch für wiederkehrende Termine zurückgeben.

6. **Declined-Handling**
   - `declined`-Termine **standardmäßig ausblenden**; sie zählen nicht als Verpflichtung.
   - Auf Wunsch ("auch abgesagte Termine zeigen") mit Kennzeichnung `~declined~` einblenden.
   - Konflikte/Dubletten (mehrere Einträge zur selben Zeit) kurz benennen, wenn sie auffallen.

7. **Feiertage und Abwesenheiten**
   - Separat ausweisen (nicht mit regulären Terminen mischen).
   - Abwesenheiten des Teams kurz benennen (wer, wie lange).
   - Feiertage markieren und bei Tagesplanung berücksichtigen.
   - **Eigene Abwesenheit ist Pflicht-Check bei Slot-Vorschlägen:** Wenn ein Termin/Slot vorgeschlagen werden soll, muss vorher der Abwesenheitskalender (`Abwesenheitskalender troii Software GmbH`) für jeden Kandidatentag geprüft werden. Eintrag „Bernhard Danecker abwesend" oder „... Feiertag" überschreibt jeden vermeintlich freien Slot im `primary` — der Hauptkalender enthält ganztägige Urlaubstage in der Regel nicht. Tage mit eigenem Eintrag werden nicht als Vorschlag ausgegeben.

8. **Ausgabe**
   - Pro Tag strukturiert (Wochentag + Datum als Überschrift).
   - Termine chronologisch.
   - Format pro Termin: Zeit, Titel, ggf. Ort, ggf. Teilnehmer (wenn nicht Routine).
   - Am Ende: Abwesenheiten und Feiertage separat.
   - Auffälligkeiten kurz benennen (parallele Termine, Konflikte, ungewöhnlich dichte Blöcke) — ohne zu interpretieren.

## Technische Hinweise

- `list_events` akzeptiert keinen Feld-Filter serverseitig. Filtern passiert clientseitig mit `jq`.
- Standard-`jq`-Pattern für destillierte Ausgabe (Attendees nur bei Einzelterminen):
  ```
  jq '[.events[] | {summary, start: (.start.dateTime // .start.date), end: (.end.dateTime // .end.date), location, responseStatus: ([.attendees[]? | select(.self==true) | .responseStatus] | first), organizer: .organizer.email, htmlLink, recurring: (.recurringEventId != null), attendees: (if .recurringEventId then null else [.attendees[]? | {email, displayName, responseStatus}] end)}]'
  ```
- Bei Truncation-Warnung: File nicht vollständig lesen, sondern direkt via `jq` auf das File anwenden.

## Konventionen

- Destillation vor Vollständigkeit — aber nichts Relevantes verlieren
- Kalendertitel wörtlich übernehmen; Meeting-Titel nicht normalisieren oder kürzen
- Keine Relevanz-Bewertung von Terminen; nur Auffälligkeiten (Konflikte, Parallelen) benennen
- Bewertung/Planung erfolgt in nachgelagerten Skills (z.B. `journal-daily-preparation`)
