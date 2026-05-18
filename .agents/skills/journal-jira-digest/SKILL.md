---
name: journal-jira-digest
description: Verdichtet Jira-Aktivität für einen Zeitraum zu signalstarken Änderungen (Statuswechsel, Blocker, Übergaben, Rückfragen) für das Journal.
---

Erstelle eine kompakte Jira-Aktivitätsverdichtung für das Projektverzeichnis.

## Wann verwenden

- Wenn ein kompakter Überblick über Jira-Änderungen für einen Zeitraum gebraucht wird
- Wenn unklar ist, welche Jira-Änderungen wirklich Führungs- oder Entscheidungsrelevanz haben
- Vor Weekly Review oder Monatsreview als strukturierter Input
- Bei Rückfragen wie „Was hat sich seit gestern/in KWxx in Jira getan?“

Nicht verwenden:
- Für vollständige Ticketlisten oder reine Statusspiegelungen
- Wenn nur ein einzelnes Ticket geprüft werden soll

## Input

- Zeitraum (heute, gestern, Woche, konkreter Bereich) optional
- Fokus optional: Projekt, Team, Thema

Falls kein Zeitraum genannt ist: heute (`{{date}}`).

## Schritte

1. **Zeitraum und Fokus bestimmen**
   - Zeitraum aus Eingabe übernehmen.
   - Ohne Eingabe: heutiger Arbeitstag.

2. **Jira-Daten laden**
   - Workspace: `troiisoftware`.
   - Zugriff ausschließlich über Jira MCP.
   - Aktivität von Bernhard und relevante Übergaben/Blocker im Fokuszeitraum abrufen.

3. **Signal statt Spiegelung**
   - Nur Änderungen mit Führungs- oder Entscheidungsrelevanz behalten:
     - Statuswechsel mit Konsequenz
     - neue Blocker / Entblockungen
     - Übergaben oder Ownership-Wechsel
     - neue Rückfragen mit offenem Handlungsbedarf
   - Task-Kategorisierung nach Projekt / Produkt / Jira Fix Version, nicht nach meldender Person.

4. **Verdichten**
   - Ausgabe nach Abschnitten strukturieren:
     - `Statuswechsel`
     - `Blocker`
     - `Übergaben`
     - `Rückfragen`
   - Jira-Issues nur dort verlinken, wo sie für Entscheidung, Blocker oder Übergabe relevant sind.

5. **Ablage im Journal festlegen**
   - Standard: Digest als kompakte Antwort ausgeben (keine Datei erzeugen).
   - Falls konkrete To-dos mit Tagesbezug entstehen: in passende Daily Note übernehmen.
   - Falls der Nutzer explizit dauerhafte Ablage will: relevante Punkte in bestehende Review-/Projekt-/Area-Notiz einarbeiten, keine Statusliste spiegeln.

## Regeln

- Jira ist Source of Truth für Status, Workflow und Assignees.
- Keine vollständige Statusliste ins Journal spiegeln.
- Keine Jira-Kommentare oder Jira-Schreiboperationen ohne explizite Aufforderung.

## Ausgabe

- Kompakter Digest für den Zeitraum
- Optional: übernommene Daily-Tasks und ggf. aktualisierte Kontextnotizen
