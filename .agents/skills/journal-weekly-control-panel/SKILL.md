---
name: journal-weekly-control-panel
description: Erzeugt eine temporäre Wochen-Arbeitsansicht aus Daily Notes, Kalender, Inbox, Projekten und Reviews. Verwende für Wochenplanung ohne neue Quelle der Wahrheit.
---

Erzeuge eine Momentaufnahme für die aktuelle oder genannte Woche.

## Quellen

- Daily Notes der Woche
- Kalendertermine der Woche via `calendar-lookup`
- Unverarbeitete Inbox-Dateien in `00-inbox/`
- Relevante aktive Projekt- und Area-Dateien
- Letzter Weekly Review

## Ausgabe

Nur als Antwort ausgeben, keine Datei anlegen, außer Bernhard verlangt ausdrücklich eine Wochenplan-Datei.
Nutze für die Antwort `assets/output-template.md`.

## Regeln

- Keine neue Task-Quelle erzeugen.
- Konkrete neue Aufgaben erst nach Bestätigung in Daily Notes eintragen.
- Inbox-Reste sichtbar machen, aber nicht automatisch klassifizieren.
- Fokus maximal 3 Punkte.
