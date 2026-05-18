---
name: journal-context-sweep
description: Vergleicht alle Projekt- und Area-Seiten (Kontextspeicher) in 03-projects/ und 04-areas/ gegen die Daily Notes der letzten Wochen und liefert einen Drift-Bericht inkl. Update-Vorschlägen. Verwende diesen Skill für einen Projekt-/Area-Audit, Drift-Check, Health-Check oder vor dem Weekly Review.
---

Audit aller Projekt- und Area-Seiten gegen die Daily Notes — Drift sichtbar machen, Update-Bedarf pro Seite benennen.

## Schritte

1. **Scope festlegen**
   - Standard-Zeitraum: letzte 4 Kalenderwochen, oder seit dem ältesten `letzter_sweep:` Datum (je nachdem was länger ist).
   - Bei Aufruf mit explizitem Zeitraum (z. B. „seit 2026-04-07") diesen verwenden.
   - Standard-Quellen: `03-projects/` **und** `04-areas/`.
   - Auf Wunsch einschränken (z. B. „nur Projekte" oder „nur Areas head-of").

2. **Projekt- und Area-Seiten erfassen**
   - Alle Dateien in `03-projects/` lesen.
   - In `04-areas/` alle aktiven Seiten lesen — also Tracker, Stand-/Status-Notizen, Followup-Checklisten und Standing-Notes. **Ausgenommen:** Meeting-Notizen (`typ: meeting`), Vorlagen (`typ: vorlage`) und Personen-Historien (`typ: personen-historie`).
   - Pro Seite notieren: Pfad, `status`, `letzter_sweep`, letzte Stand-Aussage (z. B. unter `## Aktueller Stand` oder im jüngsten Verlauf-Eintrag), offene Fragen, nächste Schritte.

3. **Daily Notes scannen**
   - Alle Daily Notes im Scope (`01-daily/YYYY/MM/`) lesen.
   - Pro Daily extrahieren: Erwähnungen von Projekten/Areas — sowohl via relativem Link (`03-projects/<datei>.md`, `04-areas/.../<datei>.md`) als auch via Schlagwort (Dateiname ohne `.md` oder `[[name]]`-Token).
   - Pro Projekt/Area eine chronologische Liste der Erwähnungen aufbauen: Datum, Stichwort, Status-Hinweis (z. B. „Retro durchgeführt", „Blocker identifiziert", „Release released", „DV unterzeichnet").

4. **Inbox-Einträge mit Statusbezug einbeziehen**
   - Aktive `00-inbox/` und archivierte `99-archive/00-inbox/` im Zeitraum auf Status-/Personenbezüge prüfen.
   - Wenn ein Inbox-Eintrag eine Statusänderung für eine Projekt-/Area-Seite enthält (z. B. Absage, Vertragsunterzeichnung, neuer Eintritt) und diese nicht auf der Ziel-Seite nachgezogen wurde: explizit als Drift ausweisen.

5. **Drift bestimmen**
   - Pro Seite vergleichen:
     - Stand auf der Projekt-/Area-Seite vs. Daily- und Inbox-Erwähnungen
     - `letzter_sweep` vs. letztes Daily-Datum
     - Aging: 14+ Kalendertage ohne Daily-Erwähnung
   - Drift-Level: `gering` / `mittel` / `hoch` / `vermutlich abgeschlossen` / `Stub (keine Aktivität)`.

6. **Update-Vorschlag pro Seite**
   - Status-Änderung? (`aktiv` ↔ `wartend` ↔ `pausiert` ↔ `abgeschlossen`)
   - Neue Verlauf-Einträge mit Datum?
   - Erledigte oder überholte offene Fragen bereinigen?
   - Neue Risiken / Blocker / Entscheidungen aufnehmen?
   - Nächste Schritte aktualisieren?

7. **Bericht ausgeben**
   - Gruppiert nach `03-projects/` und `04-areas/`, sortiert nach Drift-Level absteigend.
   - Pro Seite: kompakter Block mit aktuellem Stand, relevanten Daily-/Inbox-Erwähnungen mit Datum, konkretem Update-Vorschlag.
   - Querschnittsbefunde am Ende (z. B. mehrere Stubs ohne Aktivität, gebrochene Querverweise, ähnliche Themen über Projekte/Areas verteilt).
   - Keine Updates auf den Seiten schreiben — nur vorschlagen. Umsetzung läuft über `journal-context-update` (punktuell) oder `journal-context` (umfassend), pro Seite einzeln nach Bestätigung.

8. **`letzter_sweep` nur bei tatsächlichem Schreiben aktualisieren**
   - Wird in diesem Skill nicht gesetzt — er bleibt reiner Audit-Schritt.

## Grundregeln

- Nichts erfinden — wenn keine Daily-Erwähnung vorliegt, das so sagen.
- Querverweise präzise prüfen: gebrochene Links bei umbenannten/konsolidierten Dateien beim Update direkt mitkorrigieren lassen.
- Bei Stub-Verdacht (kein Verlauf, keine Daily-Erwähnung) Vorschlag `pausiert` oder `abgeschlossen` machen — keine Reanimations-Romanze.
- Auf jeder geprüften Projekt-/Area-Seite gefundene `- [ ]` Checkboxen explizit ausweisen — sie verletzen die Regel „keine operativen Tasks auf Projekt-/Area-Seiten". **Ausnahme:** Tracker (`typ: referenz` mit Listen-Charakter) und Followup-Checklisten (`typ: followup-checkliste`) dürfen Checkboxen behalten — dort werden sie nicht als Verstoß markiert.
