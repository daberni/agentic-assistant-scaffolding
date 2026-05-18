---
name: journal-daily-finish-off
description: Schließt den Arbeitstag ab und plant den nächsten regulären Arbeitstag. Verwende diesen Skill für Tagesabschluss, Review des heutigen Tags und Übergabe in den nächsten Tag.
---

Führe den Tagesabschluss im Projektverzeichnis durch und plane den nächsten regulären Arbeitstag.

## Ablauf

1. **Arbeitstage bestimmen**
   - Heute ist `{{date}}`, aktuelle Uhrzeit `{{time}}`.
   - Abzuschließen = letzter regulärer Arbeitstag bis inkl. heute.
   - Zu planen = nächster regulärer Arbeitstag nach dem abzuschließenden Tag.
   - Reguläre Arbeitstage sind Montag bis Freitag.
   - Feiertage und ganztägige eigene Abwesenheiten aus den Kalenderquellen nicht als Arbeitstage behandeln.
   - Teilweise Abwesenheiten und Team-Abwesenheiten als Planungskontext berücksichtigen, aber den Tag nicht automatisch überspringen.

2. **Abzuschließenden Tag reviewen**
   - Tagesnotiz des abzuschließenden Tags **direkt lesen** via `Read` auf den vollständigen Pfad `01-daily/YYYY/MM/YYYY-MM-DD.md` — **nicht** per Glob oder Existenzprüfung. Wenn die Datei nicht existiert, gibt `Read` einen Fehler zurück; dann neu anlegen.
   - **Backlog-Limit prüfen:** Falls `## Heute` mehr als **10 offene `- [ ]` Tasks** enthält, Skill abbrechen und auf `journal-task-triage` verweisen. Erst nach Triage fortfahren.
   - `## Heute` prüfen, alle Tasks daraus zeigen und offene Checkboxen interaktiv klären:
     - offen `- [ ]`: erledigt, morgen, terminiert, blockiert, delegiert, geparkt oder gelöscht?
     - erledigt `- [x]`: Folgearbeit?
   - Auf Bernhards Antwort warten, bevor die automatisierte Analyse startet.
   - Ergebnisse direkt eintragen:
     - erledigt abhaken
     - kurze Blocker-/Verschiebe-Notiz direkt unter dem Task
     - bewusst übernommene Punkte markieren
   - **Aging-Markierung:** Tasks mit `(seit DD.MM.)` Alter ≥ 7 Kalendertage bekommen ein vorangestelltes ⚠️ und werden für die nächste Tagesplanung zur Triage vorgemerkt. Tiefe Triage und aktive Entscheidung pro Task läuft über `journal-task-triage`, nicht hier.
   - **Inbox-Verarbeitung (Pflicht):** Alle Dateien in `00-inbox/` durchgehen und je nach Inhalt zuordnen — passende Daily Note, Projekt-/Area-Datei, Meeting-Notiz oder Archiv. Verarbeitete Inbox-Dateien werden verschoben oder gelöscht. Nach diesem Schritt ist `00-inbox/` leer oder enthält nur Items, die explizit dort verbleiben sollen (mit Begründung).
   - **Daily-Note-Sanity-Check:** Beiläufige, nicht terminierte Themen, die fälschlich in der Daily Note stehen, nach `00-inbox/` auslagern oder als Kontext in Projekt-/Area-Dateien verdichten.

3. **Arbeitskontext verdichten**
   - **Git-Aktivität:** Lokale Repos unter `~/Developer/` sind im Cowork-Sandbox nicht zugänglich; `gh`/`bb` CLI nicht verfügbar; kein GitHub- oder Bitbucket-MCP verfügbar. Git-Schritt im automatisierten Lauf überspringen — im Output kurz vermerken, dass Git nicht geprüft werden konnte. Bei manuellem Lauf kann Bernhard relevante Commits selbst in `## Notizen` nachtragen.
   - **Jira-Aktivität ist Pflicht** — nicht überspringen. Aktivität von Bernhard prüfen (Statuswechsel, Übergaben, neue Blocker, neue Rückfragen).
   - **JQL-Regel:** Nur echte Statuswechsel zählen — `updated >= "DATUM"` reicht nicht, weil auch reine Metadaten-Änderungen (Links, Labels) den Timestamp setzen. Stattdessen: `assignee = currentUser() AND status CHANGED ON "DATUM"` oder Changelog des Issues prüfen, bevor ein Issue als „heute abgeschlossen" gewertet wird.
   - **Releases prüfen:** Wurden heute Versionen released (Git-Tags, Jira)? Für jede Version wo Bernhard Treiber ist → Eintrag als `- [ ]` in `## Heute` der nächsten Daily Note (nicht unter `## Auf dem Radar`):
     `- [ ] Retro {PROJECT} {VERSION} terminieren → [Jira Release Report]({URL})`
   - Tagesnotiz knapp verdichten — **ohne eigene Abschnitte zu erfinden**:
     - erledigte Tasks abhaken (`- [x]`)
     - offene/verschobene Tasks mit kurzem Hinweis versehen (`→ 20.04.`, `blockiert: …`)
     - neue Erkenntnisse in `## Notizen` oder `## Auf dem Radar` einbauen
     - keine unnötige Nacherzählung, kein separater "Tagesabschluss"-Block
   - Sensible Inhalte prüfen: unnötige Details entfernen; notwendige sensible Inhalte knapp halten und in Zielnotizen mit `vertraulich` / `sensibel` markieren.

4. **Kontextablage aktualisieren**
   - Größere technische Themen in `04-areas/head-of/engineering-standards.md` unter `Gesammelte Themen`.
   - Relevante Head-of-Punkte in `04-areas/head-of/head-of-jour-fixe.md` unter `Gesammelte Punkte`.
   - Projekt-/Area-/People-Dateien nur mit Kontext, Entscheidungen, Risiken oder längerfristigen nächsten Schritten aktualisieren; keine operativen Checkbox-Duplikate erzeugen.
   - Falls ein Reflexionsabschnitt existiert und leer ist: kurz ergänzen.
   - Nächste logische Schritte aus Erledigtem für die Folgetagsplanung ableiten.

5. **Projekt-Erwähnungen prüfen**
   - Die abzuschließende Daily Note nach Bezügen zu `03-projects/<datei>.md` durchsuchen (relative Links und Schlagworte).
   - Pro getroffenem Projekt entscheiden:
     - **Stand-Update fällig** → kurzen Eintrag unter `## Verlauf` oder `## Aktueller Stand` der Projektseite ergänzen (`- **YYYY-MM-DD:** …`), bei Bedarf Status, offene Fragen oder nächste Schritte mitziehen, `letzter_sweep:` im Frontmatter aktualisieren.
     - **kein Update nötig** → bewusst überspringen, nichts schreiben.
   - Keine operativen Checkboxen auf die Projektseite duplizieren — die bleiben in der Daily Note.

6. **Nächsten Arbeitstag planen**
   - Zieltag zuerst im Verzeichnis `01-daily/YYYY/MM/` prüfen: existiert dort bereits eine Notiz für den ermittelten nächsten Arbeitstag? Falls ja, diese weiterführen — keine neue anlegen.
   - Für die konkrete Planung den Skill `journal-daily-preparation` verwenden.
   - Zieltag dabei auf den ermittelten nächsten regulären Arbeitstag setzen.
   - Relevante übernommene Punkte aus dem Abschluss als `(seit DD.MM.YYYY)` in die Planung geben — Datum ist der Tag des Erstauftretens als Task.

7. **Kompakte Ausgabe**
   - Kurz ausgeben:
     - Erledigtes am abgeschlossenen Tag
     - berührte Projekte und welche Stand-Updates eingepflegt wurden
     - wichtige Termine/Besonderheiten am nächsten Arbeitstag (nur signalstarke Termine)
