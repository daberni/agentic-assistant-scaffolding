---
name: journal-inbox
description: Erfasst beiläufige, unsortierte oder noch nicht terminierte Informationen im Journal-Vault Inbox-Ordner. Verwende diesen Skill wenn etwas erwähnt wird, das noch keinen konkreten Tagesbezug hat.
---

Erfasse den Inhalt schnell in `00-inbox/`.

## Grundregel

- Unklar, beiläufig oder nicht terminiert -> `00-inbox/`
- Konkreter Task mit Tagesbezug -> passende Daily Note
- Nicht klassifizieren und keine Aufgabe erzwingen, wenn noch keine konkrete Aktion existiert.

## Triage beim Erfassen

Vor jedem Inbox-Eintrag prüfen, wo das Item wirklich hingehört:

- Hat das Item einen klaren Tagesbezug (heute, morgen, konkretes Datum)? → direkt in die passende Daily Note, nicht in die Inbox.
- Existiert eine passende Projekt-/Area-/Meeting-Notiz, die das Item als Kontext aufnimmt? → dort ergänzen, nicht in die Inbox.
- Bleibt das Item beiläufig, unklar oder ohne klares Ziel? → erst dann in `00-inbox/`.

Inbox ist der Fallback, nicht der Standard. Inhalte, die ohne Triage in die Daily Note rutschen, machen die Daily Note unhandlich; Inhalte, die ohne Triage in die Inbox rutschen, sammeln sich dort als Müllhalde.

## Schritte

0. **Vorprüfung:** Zuerst im Journal nach bestehenden Notizen zum Thema suchen (`rg -rl` über `04-areas/`, `03-projects/`, `02-meetings/`, `00-inbox/`). Existiert bereits eine passende Notiz → dort ergänzen, keine neue Inbox-Notiz anlegen.

1. **Dateiname:** `00-inbox/{{date}}-[kurzer-titel-als-slug].md`

2. **Datei erstellen:** Verwende exakt `assets/template.md`.

3. **Bestätigung:** "Erfasst: `00-inbox/[dateiname]`"

Kein Klassifizieren, kein Umstrukturieren — einfach schnell festhalten. Das Verarbeiten erfolgt separat.
