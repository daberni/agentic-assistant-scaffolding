---
name: journal-jfx-preparation
description: Bereitet die Software-Development- und Infrastruktur-Sections für das monatliche troii-weite Jour Fixe Dokument vor. Verwende diesen Skill wenn du das JFx Dokument vorbereiten willst, einen Monatsüberblick für das JFx brauchst, oder den SE-Beitrag zum Jour Fixe formulieren willst.
---

Erstelle einen Draft für die **Software Development**- und **Infrastruktur**-Sections im troii JFx Google Doc.

## Kontext

Das troii Jour Fixe ist ein monatliches Meeting aller Bereichsleiter. Bernhard verantwortet dort zwei Sections:
- **Software Development** — strategische Technikthemen, Architekturentwicklung, AI-Adoption, Tooling, Team-Initiativen
- **Infrastruktur** — IaC-Fortschritt, Platform-Initiativen, GitHub-Migration, Bots & Agents

**Nicht in Bernhards Scope** (Produktteam schreibt das selbst):
- Neue Produktfeatures und Produktroadmap
- Einzelne Bugfixes oder Ticket-Abschlüsse
- BAU-Releases, Retros und Release-Statistiken
- Produktspezifische Metriken

## Schritte

### 1. Link zum aktuellen JFx Dokument erfragen

**Bevor irgendetwas anderes passiert:** Frage Bernhard nach dem Link zum aktuellen JFx Google Doc, falls er nicht bereits in der Anfrage mitgegeben wurde. Ohne diesen Link nicht weitermachen.

### 2. Periode bestimmen

Lies `04-areas/head-of/head-of-jour-fixe.md` und ermittle:
- Datum des **letzten JFx** (aus der Meeting-Tabelle)
- Link zum **letzten JFx Google Doc**

Periode = letztes JFx-Datum bis heute ({{date}}).

### 2. Letztes JFx Dokument lesen

Öffne das letzte JFx Google Doc über Google Drive MCP und lies **nur** die Sections:
- Software Development
- Infrastruktur

Zweck: Stil, Sprache und Abschnittstruktur als Vorlage übernehmen. Die Abschnittsnamen aus dem letzten Dokument sind die Basis für das neue.

### 4. Aktuelles JFx Dokument prüfen

Öffne das aktuelle JFx Google Doc (Link aus Schritt 1) und prüfe **nur**, ob in den Sections Software Development und Infrastruktur bereits Inhalt steht — um keine Duplikate zu erzeugen.

**Wichtig:** Den vorhandenen Inhalt nicht als Inspirationsquelle verwenden. Der Draft entsteht ausschließlich aus den Journal-Quellen in Schritt 5. Wenn das Dokument bereits befüllt ist, trotzdem einen eigenständigen Draft auf Basis der Journal-Quellen erstellen und am Ende darauf hinweisen, dass der Abgleich mit dem bestehenden Inhalt Bernhard überlässt.

### 5. Journal-Quellen für die Periode lesen

Lies parallel (alle relevanten Quellen für die Periode):

**a) Weekly Reviews**
`06-reviews/weekly/` — alle Reviews, deren Datum in die Periode fällt.
Achte auf: technische Entscheidungen, laufende Initiativen, Architekturthemen, AI-Adoption, Teamthemen mit technischem Bezug.

**b) Relevante Meeting-Notizen**
`02-meetings/` — Meetings der Periode mit technischem Inhalt (z.B. Architektur-Workshops, GitHub-Migration-Status, Frontend-Workshops, Infra-Termine).
Nur lesen wenn der Titel auf technische Inhalte hindeutet.

**c) Aktive Projekte**
`03-projects/` — lies Projektdateien, die in der Periode aktiv waren und Technik-relevanten Content haben. Insbesondere: `github-migration.md`, `troii-days-2026.md` und weitere aktive technische Initiativen.

**d) Area-Kontext**
`04-areas/head-of/head-of-jour-fixe.md` → Dauerthemen und offene Punkte, die noch nicht abgehandelt sind.

### 6. Filtern: Was ist JFx-würdig?

Behalte nur Themen die mindestens eines dieser Kriterien erfüllen:
- **Strategische Entscheidung** getroffen oder anstehend (z.B. Technologiewahl, Architekturrichtung)
- **Neue Initiative** gestartet oder abgeschlossen (z.B. neues Tool eingeführt, Migration Phase X done)
- **Persistentes systemisches Thema** das das Team beschäftigt (nicht Einzelbugs, sondern Muster)
- **AI-Adoption im Team** — neue Tools, Prozesse, Workflows mit AI
- **Platform/Enabler-Fortschritt** der alle Projekte betrifft

Raus:
- Einzelne Jira-Tickets, Bugfixes, Hotfixes
- BAU-Aktivitäten (reguläre Releases, Retros, Dependency-Updates)
- Alles was das Produktteam selbst im JFx berichtet
- Persönliche Tasks oder MAG-Inhalte

### 7. Draft formulieren

Schreibe den Draft als **Fließtext** (kein Markdown-Bullet-Chaos, keine Ticket-Keys) — genau wie der Stil im letzten JFx-Dokument.

Für jeden relevanten Themenblock:
- 2–4 Sätze: Was wurde gemacht / wo stehen wir / was ist der nächste Schritt oder die offene Frage
- Keine Jira-Keys, keine internen Slug-Namen
- Auf Deutsch, Management-tauglich, aber technisch korrekt

**Struktur des Outputs:**

```
## Software Development

### [Abschnittsname aus letztem JFx oder neues Thema]
[Fließtext 2-4 Sätze]

### [Nächstes Thema]
[Fließtext]

...

## Infrastruktur

### [Abschnittsname]
[Fließtext]
...
```

Falls ein Thema aus dem letzten JFx nicht mehr relevant ist: weglassen.
Falls ein neues Thema hinzukommt: als eigene Subsection anlegen.

### 8. Validierungshinweise

Markiere am Ende Punkte, bei denen du dir unsicher bist oder Bernhard prüfen soll, z.B.:
- Inhalte die nur aus einem Weekly Review stammen ohne weitere Bestätigung
- Themen die im Journal als "offen" oder "in Arbeit" stehen — aktuellen Status prüfen
- Punkte die im letzten JFx standen aber in dieser Periode nicht dokumentiert wurden

### 9. Bestätigung

Gib den Draft aus. Kein Schreiben in eine Datei — der Draft geht direkt in den Chat zur Überarbeitung.
Bernhard überträgt den finalen Text selbst ins Google Doc.

## Hinweise

- **Stil-Referenz ist immer das letzte JFx-Dokument**, nicht der Stil anderer Journal-Files.
- **Infrastruktur** ist eine eigene Section im Dok — nicht unter Software Development vermischen.
- **Keine Personennamen** im JFx-Text außer es ist explizit relevant (z.B. neue Mitarbeiter).
- Wenn Codex-Sessions oder andere Quellen vorhanden sind: Inhalte daraus nur verwenden wenn sie sich mit Journal-Quellen decken.
