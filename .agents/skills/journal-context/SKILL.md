---
name: journal-context
description: Pflegt Projekt- und Area-Seiten (Kontextspeicher) im Journal. Verwende diesen Skill wenn eine Projekt- oder Area-Seite angelegt, standardisiert, aktualisiert, bereinigt, pausiert oder abgeschlossen werden soll.
---

Arbeite mit Projekt- und Area-Seiten unter `03-projects/` und `04-areas/`.

## Grundregeln

- Projekt- und Area-Seiten sind Kontextspeicher, keine operative Taskliste.
- Konkrete Aufgaben mit Tagesbezug gehören in die passende Daily Note.
- Offene Fragen, Risiken, Entscheidungen, aktueller Stand und längerfristige nächste Schritte bleiben auf der jeweiligen Seite.
- Erledigte oder überholte offene Fragen und nächste Schritte beim Update bereinigen.
- **Keine `- [ ]` Checkboxen.** Backlog-, Themen- oder Folgepunkte-Listen als Aufzählung mit `-` ohne Checkbox; operative Tasks gehören in die Daily Note, nicht auf die Projekt-/Area-Seite.
- **Ausnahme Konzept-Dokumente** (`typ: workshop`, `typ: analyse`) mit fachlichen Kriterien-Listen (z. B. DoR/DoD): ebenfalls als Aufzählung mit `-`. Checkboxen nur, wenn die Liste später live abgearbeitet wird und das Dokument selbst die Arbeitsablage ist.
- **Ausnahme Tracker und Followup-Checklisten** in `04-areas/` (`typ: referenz` mit Listen-Charakter, z.B. `onboarding-tracker.md`, oder `typ: followup-checkliste`): dürfen `- [ ]` behalten, weil die Datei selbst als Checkliste konzipiert ist. Statusänderungen aus Daily/Inbox müssen aber trotzdem nachgezogen werden.

## Scope

- `03-projects/`: alle Projekte (Ziel + Deadline).
- `04-areas/`: aktive Verantwortungsbereiche, Tracker, Standing-Notes, Followup-Checklisten. **Ausgenommen:** Meeting-Notizen (`typ: meeting`), Vorlagen (`typ: vorlage`), Personen-Historien (`typ: personen-historie`) — die werden nicht über diesen Skill gepflegt.

## Template

Für neue oder zu standardisierende Projektseiten `assets/template.md` verwenden. Nur passende optionale Frontmatter-Felder behalten. Area-Seiten haben heterogenere Strukturen — Template nur soweit übernehmen, wie es zum Charakter der Area passt (Tracker bleibt Tracker, Standing-Note bleibt Standing-Note).

Bestehende gute Struktur nicht mechanisch ersetzen. Standardisieren nur soweit es Klarheit schafft.

## Ablauf

1. Projekt-/Area-Seite identifizieren oder neuen Dateinamen als `kebab-case.md` wählen.
2. Bestehende Seite lesen und ähnliche Projekte/Areas prüfen.
3. Frontmatter ergänzen oder korrigieren (inkl. `letzter_sweep: YYYY-MM-DD`).
4. Inhalt verdichten:
   - Status aktualisieren: `aktiv`, `wartend`, `pausiert`, `abgeschlossen`
   - Entscheidungen mit Datum ergänzen
   - operative Checkboxen entfernen oder in Daily Notes terminieren (Ausnahme Tracker/Followups, siehe oben)
   - überholte offene Fragen bereinigen
   - `letzter_sweep` auf heute setzen
5. Kurz bestätigen, welche Seite geändert wurde.
