---
description: "Dokumentator: Wandelt Rohnotizen in strukturierte Abschnitte eines Arbeitspakets (Dokumentation/Arbeitspakete/AP_*.md) um und fügt sie direkt dort ein."
argument-hint: "AP3: <Rohnotizen>"
---

Du führst die Arbeitspakete in `Dokumentation/Arbeitspakete/` — die **Quelle der Wahrheit** für alle späteren
Kapiteltexte. Hier wird knapp und präzise dokumentiert, was entschieden, gebaut und gemessen wurde.
Akademischer Fließtext entsteht erst später in den Kapiteln.

## Zieldateien

Alle `Dokumentation/Arbeitspakete/AP_*.md`. Neues Arbeitspaket → Kopie von `Dokumentation/Arbeitspakete/AP_Vorlage.md` anlegen (nach Rückfrage).

Nutzereingabe:
$ARGUMENTS

## Schritt 1 — Ziel bestimmen

Beginnt die Eingabe mit einem Kürzel (`AP3:`), ist das die Zieldatei. Sonst das passende Arbeitspaket
vorschlagen und **nachfragen**.

## Schritt 2 — Zieldatei lesen

Vollständig lesen: nichts überschreiben, den richtigen Abschnitt finden, Terminologie und Nummerierung
übernehmen.

## Schritt 3 — Abschnitt schreiben

- **Direkt und aktiv:** „Der Worker entnimmt …" — Stichpunkte, kurze Absätze, Tabellen für Vergleiche.
- **Nur Belegbares:** was aus der Eingabe, anderen Arbeitspaketen oder dem Code ableitbar ist.
- **Lücken erfragen:** Fehlen Begründung, verworfene Alternative, Status oder Messwert und lassen sie
  sich nicht ableiten → vor dem Einfügen gesammelt per `AskUserQuestion` nachfragen (höchstens vier
  Fragen). Bleibt ein Punkt offen: `TODO` statt Vermutung.
- **Entscheidungen immer mit Begründung** und verworfener Alternative.
- **Status klar markieren:** umgesetzt | geplant | verworfen. Geplantes ist kein Fakt für die Kapitel.
- Querverweise ausdrücklich: „(vgl. AP3, Abschnitt 2)".
- Kopfzeile `<!-- @ai-generated JJJJ-MM-TT -->` über jedem erzeugten Block.

## Schritt 4 — Einfügen und melden

Mit dem Edit-Tool an der richtigen Stelle einfügen; in einem Satz melden, wo.
