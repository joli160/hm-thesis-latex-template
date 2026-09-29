# CLAUDE.md

Die Regeln für dieses Repository stehen werkzeugneutral in `AGENTS.md` und gelten hier vollständig:

@AGENTS.md

## Prüfervorgaben

@.claude/instructions/vorgaben.md

## Schreibkonventionen

@.claude/instructions/schreibkonventionen.md

## Slash-Commands

| Command | Wofür | Schreibt nach | Darf Inhalt ändern? |
|---------|-------|---------------|---------------------|
| `/dokumentator` | Rohnotizen → strukturierter Abschnitt in einem Arbeitspaket | `Dokumentation/Arbeitspakete/AP_*.md` | nur Notizen |
| `/kapitelschreiber` | Abschnitt direkt als LaTeX in ein Kapitel schreiben | `latex/chapters/*.tex` | ja, auf Basis von Notizen |
| `/bachelor-adjuster` | Stil, Struktur, Zitation, Abkürzungen prüfen | `latex/chapters/*.tex` | **nein** — nur formale Edits nach Freigabe |
| `/thesis-editor` | gezielte formale und inhaltliche Änderungen | `latex/chapters/*.tex` | ja, mit Rückfrage bei jeder Unklarheit |
| `/grill-me` | vor einer Aufgabe alle offenen Punkte abfragen | — | — |

Read-only-Prüfprompts für die Abgabe liegen unter `.claude/instructions/pruefprompts/`. Sie werden
einzeln in eine **frische Session** kopiert, nicht über einen Command gestartet.

## Claude-spezifisch

- **Memory:** Entscheidungen, die über eine Session hinaus gelten („Feature X wurde nie umgesetzt, nicht
  erwähnen", „Begriff Y statt Z"), gehören in den Projektkontext von `AGENTS.md` — nicht nur in die
  automatische Memory von Claude Code. So sehen sie auch andere Werkzeuge und ein Gegenleser.
- **Rückfragen** stellt Claude über das Auswahl-Tool mit konkreten Optionen statt als offene Frage.
