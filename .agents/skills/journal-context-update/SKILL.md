---
name: journal-context-update
description: Aktualisiert eine Projekt- oder Area-Seite (Kontextspeicher) im Journal-Vault. Verwende bevorzugt journal-context für umfassende Pflege; dieser Skill ist für kurze Status-, Kontext- oder Entscheidungsupdates auf Projekt- und Area-Seiten.
---

Aktualisiere eine Projekt- oder Area-Seite in `03-projects/` oder `04-areas/`.

## Schritte

1. **Ziel-Seite identifizieren:** Welches Projekt oder welche Area? Falls unklar, liste relevante Dateien in `03-projects/` bzw. `04-areas/`.

2. **Aktuelle Seite lesen.**

3. **Aktualisieren:**
   - Status auf aktuellen Stand bringen: `aktiv` | `wartend` | `abgeschlossen` | `pausiert`
   - Neue Entscheidungen ergänzen mit Datum
   - Kontext, Risiken, offene Fragen oder längerfristige nächste Schritte aktualisieren
   - Erledigte oder überholte offene Fragen bereinigen
   - Relevante Meetings und Daily Notes verlinken (relativer Pfad auf die Datei)
   - Konkrete operative Aufgaben in die passende Daily Note schreiben, nicht als parallele Projekt-/Area-Checkbox
   - `letzter_sweep: YYYY-MM-DD` im Frontmatter auf den heutigen Tag setzen

4. **Nur geänderte Abschnitte anzeigen** bevor Schreiben — kurz bestätigen lassen bei größeren Änderungen.

5. **Bestätigung:** Was wurde aktualisiert.

Keine operativen Checkbox-Duplikate. **Keine `- [ ]` Checkboxen auf Projekt-/Area-Seiten** — Backlog-/Themen-Listen als Aufzählung mit `-` ohne Checkbox darstellen, operative Tasks in der Daily Note führen.

**Ausnahme:** Tracker (`typ: referenz` mit Listen-Charakter, z.B. `onboarding-tracker.md`) und Followup-Checklisten (`typ: followup-checkliste`) dürfen `- [ ]` behalten — dort gehören Checklisten zum Zweck der Datei.

Bestehende Struktur beibehalten, außer `journal-context`-Standardisierung ist ausdrücklich gewünscht.
