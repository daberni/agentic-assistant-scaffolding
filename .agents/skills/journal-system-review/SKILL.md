---
name: journal-system-review
description: Prüft monatlich Inbox-Reste, doppelte Tasks, veraltete Projekte, Decision-Log-Kandidaten, People-Follow-ups und Skill-Reibung. Verwende für Systempflege.
---

Führe einen kompakten System Review des Journal-Systems durch.

## Zweck

Der System Review prüft, ob die Organisation noch zuverlässig funktioniert. Er erzeugt kein neues Backlog, keine parallele Aufgabenliste und keine eigene Datei.

## Quellen

- `00-inbox/`: unverarbeitete Dateien, auch ohne `status`
- `01-daily/`: wiederholt übernommene oder doppelte Checkboxen
- `03-projects/`: veraltete Projektseiten, überholte offene Fragen, fehlendes `review_am`
- `04-areas/`: Kontext, der operative Checklisten geworden ist
- People-Kontext unter `04-areas/head-of/`: fällige Cadence / `Nächstes Signal bis`
- `06-reviews/weekly/`: wiederkehrende Muster und Decision-Log-Kandidaten
- `05-resources/decision-log.md`: offene oder zu duplizierte Entscheidungen
- `.agents/skills/`: Reibung durch unklare Skill-Grenzen oder Trigger

## Ablauf

1. Zeitraum bestimmen: standardmäßig letzter vollständiger Monat, außer Bernhard nennt einen Zeitraum.
2. Quellen scannen und nur strukturelle Probleme aufnehmen.
3. Keine Inhalte erfinden; nur dokumentierte Muster verwenden.
4. Konkrete operative Aufgaben, falls nötig, in passende Daily Note terminieren.
5. Ergebnis ausschließlich als kompakte Antwort ausgeben.

## Prüffragen

- Liegen Inbox-Dateien länger als eine Woche unverarbeitet?
- Gibt es operative Checkboxen außerhalb Daily Notes?
- Werden Tasks mehrfach zwischen Daily Notes übernommen?
- Haben aktive Projekte überholte offene Fragen, Risiken oder nächste Schritte?
- Gibt es Decision-Log-Kandidaten, die nicht verdichtet wurden?
- Haben People-Kontexte fällige Cadence- oder Follow-up-Signale?
- Sind Skills überlappend, zu breit oder mit Templates im `SKILL.md` statt in `assets/`?

## Regeln

- Maximal 5 strukturelle Befunde.
- Maximal 3 Arbeitsweisen-Anpassungen.
- Keine neue operative Taskliste erzeugen.
- Keine Dateien anlegen oder ändern, außer konkrete Aufgaben nach expliziter Bestätigung in Daily Notes zu terminieren.
- Sensible Inhalte nur als Muster nennen und knapp halten.
