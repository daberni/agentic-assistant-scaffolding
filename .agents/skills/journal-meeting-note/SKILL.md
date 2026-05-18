---
name: journal-meeting-note
description: Erstellt oder pflegt Meeting-Notizen mit Kontext, Entscheidungen, offenen Fragen und Follow-ups. Verwende bei Meeting-Dokumentation und Nachbereitung.
---

Erstelle eine Meeting-Notiz unter `02-meetings/`.

## Schritte

1. **Meeting-Infos klären:** Falls nicht angegeben, frage kurz nach Titel und Teilnehmer. Datum = heute ({{date}}) falls nicht anders angegeben.
   - Falls ein Kalendertermin bereits auf eine bestehende Meeting-Notiz verweist: diese Notiz weiterführen, keine neue Datei erzeugen.

2. **Dateiname:** `02-meetings/{{year}}/{{month}}/{{date}}-[titel-als-slug].md`

3. **Rohnotizen verarbeiten:** Falls der Nutzer Rohnotizen mitgibt, extrahiere daraus:
   - Entscheidungen → `**Entscheidung:** ...`
   - Eigene Follow-ups → mit Owner und Ziel-/Prüfdatum klären, dann in passende Daily Note terminieren
   - Follow-ups anderer Personen → mit Owner und Ziel-/Prüfdatum im Meeting als Kontext nennen, nicht als eigene Checkbox
   - Offene Fragen → `- ?`
   - Unklares → `[unklar]`
   - Sensible Details → weglassen, minimieren oder im Frontmatter markieren

4. **Datei erstellen:** Verwende `assets/template.md` und fülle nur relevante Abschnitte.

5. **Eigene Follow-ups in Tagesnotiz übernehmen:** Falls eine Tagesnotiz für den relevanten Tag existiert, füge eigene konkrete Aufgaben dort unter `## Heute` oder `## Auf dem Radar` ein. Falls keine Tagesnotiz existiert, nutze `journal-daily-preparation`.

6. **Bestätigung:** Pfad der erstellten Datei + Zusammenfassung der eigenen Follow-ups.

Meeting Notes sind Protokolle und Kontextspeicher, keine Aufgabenliste.
Inhalte die mehrere Personen betreffen bei Bedarf in ein geteiltes Google Doc auslagern und in der Meeting-Notiz verlinken.
