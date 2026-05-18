---
name: journal-release-followup
description: Ermittelt Releases im Zeitraum und plant Retro-/Follow-up-Aufgaben in passenden Daily Notes mit relevanten Kontextlinks.
---

Plane Release-Follow-ups im Projektverzeichnis.

## Input

- Zeitraum optional
- Konkrete Version/Release optional

Falls nichts genannt ist: heute (`{{date}}`).

## Schritte

1. **Releases bestimmen**
   - Zeitraum oder Release aus Eingabe verwenden.
   - Relevante Quellen:
     - Git-Tags in Repos aus `05-resources/projects-and-repos.md`
     - Jira-Releases/Fix Versions im gleichen Zeitraum

2. **Relevanz filtern**
   - Nur Releases übernehmen, bei denen Bernhard Treiber ist oder Follow-up-Pflicht besteht.
   - Keine reine Release-Liste spiegeln.

3. **Follow-up in Daily Notes einplanen**
   - Zieltag bestimmen (heute oder nächster Arbeitstag mit Kapazität).
   - Task in `## Heute` der Ziel-Daily eintragen; Duplikate vermeiden.
   - Standardformat:
     `- [ ] Retro {PROJECT} {VERSION} terminieren → [Jira Release Report]({URL})`

4. **Kontext verlinken**
   - Falls relevant, auf Projekt-/Meeting-Notizen verlinken.
   - Nur verlinken, wenn der Bezug für Entscheidung oder Nachverfolgung nötig ist.

## Regeln

- Operative Aufgaben nur in Daily Notes, immer als `- [ ]` Checkbox in `## Heute`.
- Keine parallele Release-Checkliste oder Retro-Tabellen in Daily Notes aufbauen — persistente Übersichten (z.B. mehrere ausstehende API-Retros) gehören in eine Ressourcen- oder Projektdatei unter `05-resources/` oder `03-projects/`.
- Wenn ein Retro-Termin nicht stattfindet: in der nächsten Daily wieder als `- [ ]` einplanen — nie still fallen lassen.
- Jira bleibt Source of Truth für Release-Status.

## Ausgabe

- Welche Releases berücksichtigt wurden
- In welche Daily Notes Follow-up-Tasks eingetragen wurden
