---
name: journal-link-hygiene
description: Prüft und bereinigt Querverweise im Journal (gebrochene Links, veraltete Ziele, unpräzise Verweise) ohne Inhalte umzuschreiben.
---

Prüfe und bereinige Link-Hygiene im Projektverzeichnis.

## Input

- Bereich(e) optional (z.B. `01-daily`, `02-meetings`, `03-projects`)
- Zeitraum optional

Falls nichts genannt ist: zuletzt geänderte Notizen im laufenden Monat prüfen.

## Schritte

1. **Scope bestimmen**
   - Verzeichnisse und Zeitraum aus Eingabe ableiten.
   - Zielmenge der Dateien festlegen und kurz ausgeben.

2. **Links scannen**
   - Wiki-Links (`[[...]]`) und Markdown-Links auf Journal-Ziele erfassen.
   - Gebrochene oder unpräzise Ziele markieren:
     - Datei existiert nicht mehr
     - Link zeigt auf Ordner statt konkrete Notiz
     - Linktext/Ziel passt nicht mehr zum Kontext

3. **Eindeutige Fälle korrigieren**
   - Bei eindeutiger Ziel-Notiz Link direkt korrigieren.
   - Veraltete Pfade nach Umbenennungen oder Verschiebungen anpassen.
   - Präzise Direktverweise bevorzugen.

4. **Mehrdeutige Fälle markieren**
   - Wenn kein eindeutiges Ziel vorhanden ist: nicht raten.
   - Offene Punkte als „manuell klären“ in der Ausgabe auflisten.

## Regeln

- Nur Links ändern, keine inhaltliche Umschreibung der Notizen.
- Querverweise bleiben kurz und zielgenau.
- Keine neuen Dokumentstrukturen einführen.

## Ausgabe

- Liste der korrigierten Verweise
- Liste der offenen, nicht automatisch lösbaren Fälle
