---
name: journal-process-inbox
description: Verarbeitet und klassifiziert alle unbearbeiteten Inbox-Notizen im Journal-Vault. Verwende diesen Skill wenn der Nutzer die Inbox leeren, Notizen einordnen oder verarbeiten möchte.
---

Verarbeite alle unbearbeiteten Notizen in `00-inbox/`. Dieser Skill ist die vollständige Inbox-Verarbeitung; Tagesabschluss und Weekly Review machen nur Kurzchecks, außer Bernhard verlangt explizit Verarbeitung.

## Schritte

1. **Inbox scannen:** Lies alle `.md` Dateien in `00-inbox/`. Als unbearbeitet gelten Dateien mit `status: neu` und Dateien ohne `status`.

2. **Für jede Notiz entscheiden:**

   | Was es ist | Wohin |
   |------------|-------|
   | Aufgabe mit Tagesbezug | In passende Tagesnotiz unter `## Heute` oder `## Auf dem Radar` |
   | Projekt-/Area-Kontext | Bestehende Projekt-/Area-Datei ergänzen, ohne operative Checkbox-Duplikate |
   | Idee / Projekt | `03-projects/` (neue Datei) oder bestehende Projektseite |
   | Referenz/Quelle | `05-resources/` |
   | Meeting-/People-Kontext | Passende Meeting- oder People-Datei ergänzen |
   | Nicht mehr relevant | `99-archive/` |

3. **Für jede Notiz:**
   - Inhalt an Zielort verschieben, verdichten oder verlinken.
   - Nach Verarbeitung die Inbox-Datei archivieren — dafür `journal-archive` verwenden.
   - Konkrete Aufgaben nur in Daily Notes als `- [ ]` formulieren.
   - Task-Kategorisierung in Daily Notes nach Projekt / Produkt / Jira Fix Version, nicht nach meldender Person.

4. **Taktung beachten:**
   - Daily Shutdown: nur offensichtliche Fehlablagen verschieben oder sichtbar machen.
   - Weekly Review: Inbox-Reste prüfen; bei Verarbeitung diesen Skill vollständig laufen lassen.
   - Monatlicher System Review: liegen gebliebene Inbox-Dateien als Strukturproblem markieren.

5. **Zusammenfassung:** Liste was wo eingeordnet wurde.

Keine Dopplungen erzeugen. Prüfe ob ähnliche Notizen bereits existieren.
