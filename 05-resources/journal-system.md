# Journal-System: Struktur und Methodik

Diese Datei erklärt, warum das Journal so aufgebaut ist. Globale Leitplanken bleiben in `AGENTS.md`; operative Regeln und wiederkehrende Abläufe liegen in Skills.

## Designprinzipien

1. **Eine operative Task-Quelle:** Konkrete Aufgaben stehen nur in Daily Notes. Projekt-, Meeting-, People- und Review-Dateien speichern Kontext, Entscheidungen, Risiken und Muster.
2. **Erst erfassen, dann klären:** Beiläufige oder unklare Informationen landen in `00-inbox/`. Erst bei der Verarbeitung wird entschieden, ob daraus Task, Kontext, Referenz, Entscheidung oder Archiv wird.
3. **Kontext dort pflegen, wo er später gebraucht wird:** Projekte in `03-projects/`, Verantwortungsbereiche in `04-areas/`, People-Kontext unter `04-areas/head-of/`, stabile Referenzen in `05-resources/`.
4. **Reviews sind Reflexion, nicht Backlog:** Weekly und Monthly Reviews beschreiben Ergebnisse, offene Muster und Lernpunkte. Neue operative Aufgaben werden in Daily Notes terminiert.
5. **Entscheidungen werden verdichtet:** Tages- und Meeting-Notizen erfassen Entscheidungen nah am Geschehen; Weekly Reviews markieren Kandidaten; `05-resources/decision-log.md` enthält nur langlebige Entscheidungen.
6. **Datensparsamkeit:** Sensible Details werden vermieden oder knapp und zweckgebunden markiert.
7. **Kleines Kontextfenster durch Querverweise:** Notizen bleiben fokussiert und verweisen auf führende Kontext-Notizen, statt denselben Inhalt mehrfach zu führen.

## Ordnerlogik

| Ordner | Zweck | Methodischer Bezug |
|--------|-------|--------------------|
| `00-inbox/` | Rohes, beiläufiges, unsortiertes Material | GTD Capture, Zettelkasten Fleeting Notes |
| `01-daily/` | Tagesplanung, operative Tasks, Tageskontext | GTD Engage, Daily Log |
| `02-meetings/` | Protokolle, Entscheidungen, offene Fragen, Follow-ups | Meeting Notes / Action Items |
| `03-projects/` | Aktive Vorhaben mit Ziel, Stand, Risiken, Entscheidungen | PARA Projects |
| `04-areas/` | Laufende Verantwortungsbereiche ohne fixes Enddatum | PARA Areas |
| `05-resources/` | Stabile Referenzen, Quellen, Systemdokumentation | PARA Resources |
| `06-reviews/` | Wochen-/Monatsreflexion, Muster, Decision-Kandidaten | GTD Reflect / Weekly Review |
| `99-archive/` | Erledigtes, Überholtes, nicht mehr Aktives | PARA Archive |

## Warum nicht alles in einer Liste steht

Eine einzige Aufgabenliste wirkt sauber, wird aber schnell unzuverlässig, wenn sie Kontext, Entscheidungen, Ideen, People-Signale und echte Tasks vermischt. Deshalb trennt das System:

- Tasks: nur Daily Notes
- Kontext: Projekt-, Area-, Meeting- oder People-Dateien
- Langlebige Entscheidungen: Decision Log
- Unsortiertes: Inbox
- Reflexion: Reviews

Diese Trennung reduziert Checkbox-Duplikate und hält die Frage klar: „Was muss an welchem Tag wirklich getan werden?“

## Pflege-Taktung

| Takt | Pflege |
|------|--------|
| Laufend | Unklare Erwähnungen mit `journal-inbox` erfassen |
| Tagesabschluss | offene Checkboxes entscheiden, beiläufige Daily-Einträge in Inbox/Kontext verschieben |
| Weekly Review | Woche reflektieren, Inbox-Reste sichtbar machen, Decision-Log-Kandidaten markieren |
| Decision Log | wöchentlich oder monatlich langlebige Entscheidungen übernehmen |
| System Review | monatlich Inbox-Reste, doppelte Tasks, stale Projekte, People-Follow-ups und Skill-Reibung als reine Antwort prüfen |
| Review der Reviews | monatlich Arbeitsmuster und maximal 3 Arbeitsweisen-Anpassungen extrahieren |

## Methodische Quellen

- [GTD Five Steps](https://gettingthingsdone.com/five-Steps/): Capture, Clarify, Organize, Reflect, Engage als Grundfluss für Inbox, Tagesplanung und Reviews.
- [GTD Weekly Review](https://gettingthingsdone.com/wp-content/uploads/2016/04/GTD-WeeklyReview.pdf): Inbox/Notizen regelmäßig leeren und reflektieren, ohne daraus automatisch ein neues Backlog zu machen.
- [PARA Method](https://fortelabs.com/blog/para/): Projects, Areas, Resources, Archives als einfache Top-Level-Trennung nach Nutzungszweck.
- [Johnny.Decimal](https://johnnydecimal.com/10-19-concepts/11-core/11.01-introduction/): Bestätigt die Idee stabiler, begrenzter Ablagebereiche; im Journal bewusst ohne Nummernzwang übernommen.
- [Zettelkasten / Fleeting Notes](https://zettelkasten.de/posts/concepts-sohnke-ahrens-explained/): Rohnotizen sind temporär und werden später in dauerhaft brauchbare Notizen überführt.
- [Michael Nygard: Documenting Architecture Decisions](https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions): Entscheidungsprotokolle sollen klein, nachvollziehbar und auf langlebige Entscheidungen fokussiert sein.
- [ADR GitHub Organization](https://adr.github.io/): Decision Logs als Sammlung einzelner Entscheidungsrecords mit Kontext und Konsequenzen.
- [Atlassian DACI](https://www.atlassian.com/team-playbook/plays/daci): Für größere Entscheidungen Rollen, Kontext, Optionen und Outcome sichtbar machen; im Journal nur bei passenden Entscheidungen leichtgewichtig verwenden.
- [Atlassian Meeting Notes Template](https://www.atlassian.com/dam/jcr%3A60ac65dd-1a22-4f2c-b62f-66cc33906ff9/Meeting%20Notes.pdf): Teilnehmer, Themen, Action Items und Outcomes als Meeting-Grundstruktur.
- [Claude Skills: Creating custom skills](https://claude.com/docs/skills/how-to): Skills als fokussierte Workflows mit `SKILL.md` und ausgelagerten Ressourcen.
- [Claude Skills Best Practices](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices): Skills knapp halten und zusätzliche Details nur bei Bedarf laden.

## Bewusste Abweichungen

- Kein vollständiges Johnny.Decimal-System: Die vorhandenen Ordner sind stabil genug; Nummern würden aktuell mehr Pflegekosten als Nutzen bringen.
- Kein reines Zettelkasten-System: Das Journal ist ein Arbeits- und Führungsjournal, kein primäres Wissensproduktionssystem.
- Kein Decision Log für jede kleine Entscheidung: Nur langlebige Produkt-, Architektur-, HR-, Organisations-, Rollen- und Prioritätsentscheidungen werden übernommen.
- Kein Weekly Review als Aufgabenliste: Offene Punkte werden als Muster oder Kontext reflektiert; operative Aufgaben gehören in die Daily Notes.
