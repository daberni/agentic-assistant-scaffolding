---
name: journal-archive
description: Archiviert Notizen, Projekte oder andere Journal-Dateien die nicht mehr aktiv sind. Verwende diesen Skill wenn etwas abgeschlossen, überholt oder nicht mehr relevant ist.
---

Verschiebe die Datei in den passenden Unterordner von `99-archive/`.

## Struktur

Das Archiv spiegelt die Ursprungsstruktur des Journals:

| Herkunft | Archivziel |
|----------|------------|
| `00-inbox/` | `99-archive/00-inbox/` |
| `01-daily/` | `99-archive/01-daily/` |
| `02-meetings/` | `99-archive/02-meetings/` |
| `03-projects/` | `99-archive/03-projects/` |
| `04-areas/` | `99-archive/04-areas/` |
| `06-reviews/` | `99-archive/06-reviews/` |

## Schritte

1. **Unterordner prüfen:** Falls der Zielordner noch nicht existiert, anlegen.
2. **Datei verschieben:** Original-Dateiname bleibt erhalten.
3. **Verweise bereinigen:** Falls andere Notizen auf die archivierte Datei verlinken und der Link nun irreführend ist, Verweis anpassen oder entfernen.
4. **Bestätigung:** "Archiviert: `99-archive/[pfad]`"
