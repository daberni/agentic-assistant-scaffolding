---
name: journal-monthly-review
description: Erstellt einen Monatsreview als Verdichtung aus Weekly Reviews, Systemsignalen und Decision-Log-Kandidaten ohne operatives Backlog.
---

Erstelle oder aktualisiere einen Monatsreview im Projektverzeichnis.

## Input

- Monat optional (`YYYY-MM`)

Falls nichts genannt ist: letzter vollständiger Monat.

## Schritte

1. **Monat bestimmen**
   - Zielmonat aus Eingabe oder Standard ableiten.
   - Datei: `06-reviews/monthly/YYYY-MM.md`.

2. **Quellen laden**
   - Weekly Reviews des Zielmonats (`06-reviews/weekly/`).
   - Relevante Daily-/Meeting-/Projektkontexte nur zur Plausibilisierung.
   - Systemsignale aus `journal-system-review` (oder äquivalenter Monatsprüfung) übernehmen.
   - Decision-Log-Kandidaten aus Weekly Reviews und offenen Verdichtungen sammeln.

3. **Monatsreview schreiben**
   - Für neue Datei `assets/template.md` verwenden.
   - Fokus auf Muster, Ursache-Wirkung und Führungsimplikationen.
   - Maximal 3 Arbeitsweisen-Anpassungen unter „Fokus nächster Monat“.

4. **Backlog vermeiden**
   - Keine operative Checkboxliste im Monatsreview aufbauen.
   - Falls konkrete tagesbezogene Tasks nötig sind: in passende Daily Notes terminieren.

## Regeln

- Keine Outcomes erfinden; nur dokumentierte Evidenz verwenden.
- Sensible Themen nur knapp, zweckgebunden und als Muster notieren.
- Decision-Log-Kandidaten markieren, aber nicht automatisch duplizieren.

## Ausgabe

- Pfad des Monatsreviews
- Kompakte Monatszusammenfassung in 3-5 Sätzen
