---
name: journal-decision-log
description: Verdichtet langlebige Entscheidungen aus Daily Notes, Meeting Notes und Weekly Reviews in ein Entscheidungsprotokoll. Verwende diesen Skill für wöchentliche oder monatliche Decision-Log-Pflege.
---

Pflege ein Decision Log im Journal. Falls noch keines existiert, lege `05-resources/decision-log.md` an.

## Welche Entscheidungen aufnehmen

Aufnehmen:
- Produkt- und Architekturentscheidungen
- HR-, Rollen- und Organisationsentscheidungen
- Prioritäts- oder Scope-Entscheidungen mit späterer Relevanz

Nicht aufnehmen:
- Kleine Tagesentscheidungen
- Reine Terminabsprachen
- Jira-Statusspiegelungen ohne eigenständige Entscheidung

## Quellen

1. Weekly Reviews: `## Decision-Log-Kandidaten` als bevorzugter Eingang
2. Daily Notes und Meeting Notes: `**Entscheidung:**` zur Prüfung und Quellenverlinkung
3. Projekt-/Area-Dateien: langlebige dokumentierte Entscheidungen

## Format

Nutze für neue Einträge `assets/entry-template.md`.

## Ablauf

1. Kandidaten aus Weekly Reviews sammeln.
2. Gegen Daily/Meeting/Projekt-/Area-Quelle plausibilisieren.
3. Nur langlebige Entscheidungen übernehmen.
4. Bereits vorhandene Entscheidungen aktualisieren oder als ersetzt markieren.

## Regeln

- Keine Entscheidung erfinden oder aus Kalenderterminen ableiten.
- Bestehende Entscheidungen aktualisieren statt duplizieren.
- Quelle immer verlinken.
- Sensible Entscheidungen knapp halten und bei Bedarf `vertraulich` beachten.
- Das Decision Log ist die Verdichtung nach Daily/Meeting/Weekly, keine zusätzliche manuelle Tagespflege.
