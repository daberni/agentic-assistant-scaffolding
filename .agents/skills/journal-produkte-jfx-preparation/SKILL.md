---
name: journal-produkte-jfx-preparation
description: Bereitet den Produkt Jour Fixe (Di 10:30) vor — arbeitet aus den Journal-Quellen heraus, welche Punkte Bernhard für die anderen Teilnehmer ins Agenda-Doc eintragen sollte. Verwende diesen Skill für die wöchentliche Prod-JFx-Vorbereitung oder wenn explizit nach „Prod-JFx", „Produkte Jour Fixe" oder „Produkt-JFx" gefragt wird.
---

Bereite den **Produkt Jour Fixe (Di 10:30)** im Projektverzeichnis vor. **Output ist eine Liste von Punkten, die Bernhard fürs Agenda-Doc vorzubereiten hat — keine Status-Zusammenfassung der Periode.**

## Grundprinzip

Der Termin selbst geht den Stand durch — der Draft braucht das nicht zu wiederholen. Andere Teilnehmer pflegen ihre Themen selbst ein. Bernhard trägt nur ein, was die anderen vor dem Termin wissen sollen oder wozu er Input/eine Entscheidung aus der Runde braucht.

**Liefere also:**
- Entscheidungen, die Bernhard von der Runde braucht
- Hinweise, die das Team vor dem Termin kennen muss (z.B. bewusste Parkentscheidungen, Übergaben)
- Offene Fragen / Blocker, die Bernhard auf die Agenda heben will
- Strukturelle Cross-Cuts, die er als eigenen Agendapunkt setzen will

**Liefere nicht:**
- Release-Liste der Periode
- Pipeline-Übersicht (steht in Jira)
- Retro-Outcomes, die bereits im Doc stehen oder schon eingepflegt wurden (nur neu hinzukommende erwähnen, falls Entscheidung daran hängt)
- Themen aus anderen Verantwortungsbereichen, zu denen Bernhard nichts einbringt

## Scope

**In:** Produkte aus Bernhards Verantwortung
- [timr](../../../04-areas/software/timr.md) — Kernprodukt
- [tour](../../../04-areas/software/tour.md) — Car Mileage Tracking
- Zugehörige Produkt-Projekte unter `03-projects/` (z.B. `timr-api-v1.md`, `timr-sdk.md`, `troii-days-2026.md`, `troii-days-prozess-workshop.md`, `troii-days-prozess-soll-ist-analyse.md`)

**Out:**
- Dienstleistungs-/Kundenprojekte (BAWAG Markets, Hello bank!, Weigel, Moosmeier, WFL, Impex, etc.) — gehören in andere Schienen
- Head-of-/People-/MAG-Themen — gehören ins troii-JFx oder Head-of-JF
- BAU-Einzelbugs ohne Produktentscheidung

## Ablauf

1. **Periode bestimmen**
   - Letzter Prod-JFx: Kalender-Termin Di 10:30 in der vorigen Woche oder Datum am letzten gepflegten Abschnitt des Agenda-Docs.
   - Periode = letzter Prod-JFx bis Zieltermin.

2. **Agenda-Doc immer zuerst laden**
   - Quelle: [`04-areas/software/timr.md` → Meeting-Zuordnung](../../../04-areas/software/timr.md) → [Projekt und Produktplanung GDoc](https://docs.google.com/document/d/1zmQwU0nqxMb9ExZk_dRO5bPs8QI1riq9euKDqR3zCIY/edit)
   - Über Google Drive MCP laden, Section-Struktur und bestehenden Inhalt prüfen.
   - **Wichtig:** bestehenden Inhalt nicht als Inspirationsquelle für den eigenen Draft verwenden — nur Duplikate vermeiden. Der Draft entsteht aus den Journal-Quellen.

3. **Produkt-Verantwortungsbereich prüfen / aktualisieren**
   - Pro Produkt-Area und produkt-relevantem Projekt:
     - Letzte Änderungen seit `letzter_sweep` durchgehen
     - Offene Entscheidungen, Risiken, Statuswechsel sammeln
     - Stand-Update auf der Seite ergänzen wenn Bewegung passiert ist (`letzter_sweep:` mitziehen)
   - Quellen kreuzweise nutzen: Daily Notes der Periode, Weekly Review der Periode, Meeting-Notizen unter `02-meetings/`.

4. **Releases seit letztem Prod-JFx**
   - Jira-Query pro Produkt-Key (TIMR, TAO, TAT, TIMRIOSOFF, TOUR, TOURA):
     - `project = <KEY> AND fixVersion in releasedVersions() AND released >= "<letzter-prod-jfx>"`
   - Kompakter Versionsüberblick: pro Release-Version 1–2 Sätze, wichtigste Themen oder offene Punkte.

5. **Pre-Release / Beta / RC in der Pipeline**
   - Was steht aktuell zur Auslieferung an? Versionen mit `released = false` und aktiven Issues in den Produkt-Projekten.
   - Kurz: Was kommt, Status, Risiken.

6. **Retro-Outcomes einpflegen**
   - Retros der Periode aus Kalender (`Retro` im Titel) sammeln.
   - Pro Retro Miro-Board über Miro-MCP (`board_list_items`) auslesen — Board-Link in der Termin-Beschreibung.
   - **Thematisch synthetisieren statt Sticky-Notes aufzählen.** Pro Retro:
     - 1 Satz „Was lief gut" — verdichtet, nicht Liste
     - 2–4 Punkte „Schwierig / Erkenntnis" — Themen zusammenfassen, nicht jedes Sticky einzeln
     - Gemeinsame Muster über mehrere Retros zusammenziehen (z.B. mehrere Retros adressieren dasselbe Tooling-Problem → einmal als Cross-Cut benennen)
   - Title pro Retro aus „Notiz für PZ"-Sticky übernehmen, falls vorhanden.

7. **Produktrelevante Engineering-Standards / Cross-Cuts**
   - [`04-areas/head-of/engineering-standards.md`](../../../04-areas/head-of/engineering-standards.md) → „Gesammelte Themen" prüfen
   - Nur Punkte mitnehmen, die produktrelevant sind (AI-Workflows, Tooling, Architektur, Refactoring-Patterns). Reine Head-of-Themen weglassen.

8. **Punkte für Bernhards Eintrag filtern**
   - Aus allem Gesammelten **nur** behalten, was die anderen vor dem Termin wissen müssen oder wozu Bernhard Input braucht.
   - Pro Punkt klar machen: **Was ist die Entscheidung / der Hinweis / die offene Frage?** Nicht: was wurde gemacht.
   - Reihenfolge nach inhaltlicher Nähe (z.B. alles zu API v1 zusammen, alles zu Mobile zusammen), nicht nach Releases/Pipeline/Retro.
   - **Stil:** knapp, ein Punkt pro Thema, max. 1–3 Sätze. Kein Bullet-Chaos, kein Ticket-Key-Listing.
   - Releases/Pipeline/Retro-Outcomes nur dann erwähnen, wenn daran eine konkrete Entscheidung/Frage/Übergabe hängt.

9. **Validierungshinweise**
   - Punkte markieren, bei denen Unsicherheit besteht oder Bernhard prüfen soll.
   - Themen die im letzten Prod-JFx-Abschnitt standen, in der aktuellen Periode aber nicht dokumentiert wurden: explizit hinweisen.

10. **Bestätigung**
    - Draft im Chat, kein direktes Schreiben ins GDoc.
    - Bernhard überträgt den finalen Text selbst.

## Hinweise

- **Output ist Bernhards Vorbereitungsliste, kein Periodenbericht.** Im Zweifel weglassen — der Termin geht den Rest gemeinsam durch.
- **Dienstleistungsprojekte konsequent ignorieren** — auch wenn sie technisch interessant sind. Sie haben eigene Termine (z.B. PM-JFx Mo).
- Personennamen sparsam — nur wenn explizit relevant (z.B. Übergabe, Verantwortungswechsel, Input-Anforderung an konkrete Person).
- Bei Retro-Synthese: nur dann ein Punkt für Bernhard, wenn daraus ein strukturelles Thema wird, das er auf die Agenda heben will.
