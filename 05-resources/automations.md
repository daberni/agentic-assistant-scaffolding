---
typ: referenz
letzter_sweep: 2026-05-18
---

# Automatisierungen

Claude Cowork unterstützt **Scheduled Tasks** — wiederkehrende Aufgaben, die automatisch zur eingestellten Zeit gestartet werden. Das System fragt von selbst nach, statt darauf zu warten, dass man dran denkt.

Zwei Tasks reichen, um den Journal-Rhythmus zu tragen:

---

## 1. Tagesroutine

Werktäglich morgens — das System pingt einen, bereitet die Tagesnotiz vor und fragt die Punkte für heute ab.

| Feld | Wert |
|---|---|
| **Name** | Tagesroutine |
| **Description** | Routine für tägliche Tasks und Tagesüberblick |
| **Prompt** | `Führe den Skill `journal-daily-note` aus. Heute ist {{date}}, aktuelle Uhrzeit: {{time}}. Gestalte die Ausführung interaktiv, auch wenn es automatisiert gestartet wird!` |
| **Project / Folder** | dieser Vault |
| **Frequency** | Weekdays |
| **Time** | 08:45 |

**Was passiert:** `journal-daily-note` routet je nach Uhrzeit auf den richtigen Sub-Skill:

- Vor 13:00 → `journal-daily-preparation` (Tagesvorbereitung)
- Ab 13:00 → erst `journal-daily-finish-off` (Tagesabschluss), dann `journal-daily-preparation` für den nächsten Arbeitstag

Damit deckt **eine** Automation sowohl Morgen- als auch Spätstart ab. Wer um 11:00 erst startet, kriegt die Tagesplanung. Wer um 16:00 das System öffnet, kriegt Tagesabschluss + nächste Tagesplanung.

---

## 2. Weekly Review

Freitagnachmittag — der Wochenrückblick wird vorbereitet, Inhalte aus den Daily Notes destilliert.

| Feld | Wert |
|---|---|
| **Name** | Weekly Review |
| **Description** | Erstellt den Wochenreview aus Daily Notes und Kalender |
| **Prompt** | `Führe den Skill `journal-weekly-review` aus. Heute ist {{date}}. Bereite den Review der aktuellen Kalenderwoche aus den Daily Notes und Kalender-Einträgen vor.` |
| **Project / Folder** | dieser Vault |
| **Frequency** | Every Friday |
| **Time** | 17:00 |

**Was passiert:** Skill liest die Daily Notes der Woche, destilliert Ergebnisse, Erfolge, Offen-Geblieben, Entscheidungen und Erkenntnisse, schlägt einen Fokus für die nächste Woche vor. Der Review ist Reflexion, kein Backlog — und nicht zum „abarbeiten", sondern zum durchgehen und gegebenenfalls schärfen.

---

## Einrichten in Claude Cowork

1. **Settings** → **Scheduled tasks** öffnen
2. **Add scheduled task** klicken
3. Felder oben übernehmen — Project auswählen, Frequency setzen
4. **Save**

Die Tasks laufen mit einem kleinen Randomized-Delay (wenige Minuten), das ist kein Bug.

---

## Optional: Monthly Review

Wer den Monatsrhythmus auch automatisieren will, kann zusätzlich eine Task am 1. Werktag des Monats anlegen:

| Feld | Wert |
|---|---|
| **Name** | Monthly Review |
| **Description** | Monatsreview aus Wochenreviews und Daily Notes |
| **Prompt** | `Führe den Skill `journal-monthly-review` aus. Heute ist {{date}}. Bereite den Review des Vormonats vor.` |
| **Frequency** | Monthly (1. Werktag) |
| **Time** | 10:00 |

---

## Faustregeln

- **Eine Automation pro Routine, nicht eine pro Sub-Workflow** — der Routing-Skill (`journal-daily-note`) sortiert intern, was zu tun ist
- **Prompts kurz halten** — der eigentliche Inhalt steckt im Skill, nicht im Scheduled-Task-Prompt
- **„Interaktiv"-Hinweis im Prompt** wenn der Skill Rückfragen stellt — sonst läuft der Skill durch ohne dass Bernhard antwortet
- **`{{date}}` und `{{time}}` als Platzhalter** — werden zur Ausführungszeit ersetzt, damit der Skill den richtigen Tagesbezug hat
