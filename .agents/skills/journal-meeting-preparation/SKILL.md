---
name: journal-meeting-preparation
description: Bereitet Meetings aus Kalender- und Journal-Kontext vor, führt bestehende Meeting-Notizen weiter und erstellt konkrete Vorbereitungsblöcke.
---

Bereite ein Meeting im Projektverzeichnis vor.

## Input

- Datum, Terminname oder Produkt/Projektkontext (optional)
- Falls kein Input kommt: nächster relevanter Termin ab heute (`{{date}}`)

## Schritte

1. **Zieltermin bestimmen**
   - Termin aus Eingabe wählen oder den nächsten relevanten Kalendereintrag für den Zieltag bestimmen.
   - Kalenderdaten über `calendar-lookup` laden.
   - Titel aus Kalender wörtlich übernehmen.

2. **Meeting-Kontext laden**
   - Relevante Area-Datei unter `04-areas/software/` prüfen.
   - Abschnitt `**Meeting-Zuordnung:**` als Quelle für Zuordnung, Teilnehmerkreis und Ablage verwenden.
   - Letzte passende Meeting-Notiz in `02-meetings/YYYY/MM/` suchen.
   - **Produkt Jour Fixe (Di 10:30):** dedizierter Skill `journal-produkte-jfx-preparation` — nicht hier weitermachen.
   - Wenn der Inhalt aus dem Terminname allein nicht klar erkennbar ist (z.B. Refinement, Retro, generischer Name): Links aus Terminbeschreibung oder -notiz abrufen und lesen, um Themen und Agenda zu ermitteln.
   - Bei Retros mit Versionsnummer im Titel (z.B. „Retro TAO 12.12.1"): Jira-Query `project = <KEY> AND fixVersion = "<VERSION>"` ausführen und kompakten Überblick liefern — Bug-Anzahl, wichtigste Features/Stories, Anteil Dependency-Updates. Kein vollständiges Ticket-Listing nötig.

3. **Bestehende Notiz weiterführen**
   - Falls Kalendertermin oder Kontext bereits auf eine Meeting-Notiz verweist: diese weiterführen.
   - Nur wenn keine passende Notiz existiert: neue Meeting-Notiz über `journal-meeting-note`-Struktur anlegen.

4. **Vorbereitungsblöcke eintragen**
   - In die Zielnotiz die Blöcke aus `assets/preparation-block.md` einfügen oder aktualisieren.
   - Offene Punkte aus letzter Notiz, aktuellen Projekten und relevanten Jira-Themen verdichten.
   - Keine Statusliste spiegeln; nur entscheidungsrelevanten Kontext ergänzen.

5. **Konkrete Vorbereitungstasks terminieren**
   - Eigene, terminierte Vorbereitungsaufgaben in die passende Daily Note übernehmen.
   - Falls die Ziel-Daily fehlt: `journal-daily-preparation` nutzen.

## Regeln

- Keine doppelte Meeting-Notiz für denselben Termin erzeugen.
- Inhalte mit mehreren Beteiligten bei Bedarf in ein geteiltes Google Doc auslagern und in der Meeting-Notiz verlinken.
- Meeting-Notiz bleibt Protokoll und Kontextspeicher, keine parallele operative Aufgabenliste.

## Ausgabe

- Pfad der vorbereiteten Meeting-Notiz
- Kurze Liste der ergänzten Vorbereitungsblöcke
- Übernommene Daily-Tasks (falls vorhanden)
