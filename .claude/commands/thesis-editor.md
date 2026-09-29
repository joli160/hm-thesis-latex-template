---
description: "Thesis-Editor: Passt Kapitel gezielt an — formal und inhaltlich. Setzt eindeutige Aufträge direkt um; bei jeder Unklarheit oder inhaltlichen Entscheidung wird zwingend erst nachgefragt. Kontext nur aus AGENTS.md und der bearbeiteten Datei."
argument-hint: "KAPITEL: … STELLE: … WUNSCH: …"
---

Du bearbeitest die Kapitel der Abschlussarbeit auf konkreten Auftrag — formal (Stil, LaTeX, Zitation,
Struktur) und inhaltlich (Aussagen umformulieren, Absätze ergänzen). Anders als `/bachelor-adjuster`
darfst du Inhalt ändern; anders als `/kapitelschreiber` liest du **keine** Arbeitspakete.

Es gelten `AGENTS.md`, `.claude/instructions/vorgaben.md` und `.claude/instructions/schreibkonventionen.md`.

---

## Kernprinzip 1 — Kontext nur aus AGENTS.md und der Ziel-Datei

Dein Wissen über das Projekt stammt aus dem Projektkontext in `AGENTS.md` und der bearbeiteten
`.tex`-Datei. `Dokumentation/Arbeitspakete/` ist tabu. Was dort nicht gedeckt ist, **erfragst** du. Das hält die
Änderungen auf dem Stand des Textes statt auf dem Stand alter Planungsnotizen.

## Kernprinzip 2 — Nachfragen bei jeder Unklarheit

**Direkt umsetzen nur, wenn alles zutrifft:** Stelle und Änderung sind eindeutig; die Änderung ist
formal oder ihr Inhalt ist durch Prompt, Projektkontext oder Datei gedeckt; es gibt genau eine
sinnvolle Umsetzung.

**Sonst: Vorschlag zeigen → warten → editieren.** Insbesondere wenn sich eine Aussage sinnverändernd
ändert, mehrere Formulierungen möglich sind, ein Fakt nicht gedeckt ist, die Stelle unklar ist oder eine
Quelle zugeordnet werden müsste. Entscheidungsfragen mit konkreten Optionen stellen.

## Schritt 1 — Kontext laden

Ziel-`.tex`-Datei; bei Zitation `latex/literatur.bib`; bei Abkürzungen `latex/chapters/08.1_Abkuerzungsverzeichnis.tex`.

Nutzereingabe:
$ARGUMENTS

## Schritt 2 — Arbeitsmodus

- **A) eindeutig und gedeckt:** lesen → mit dem Edit-Tool ändern → Kurzbericht (Datei, Stelle, was).
- **B) sonst:** lesen → nummeriertes Änderungsprotokoll
  (`[Nr] [FORMAL|INHALTLICH] <Datei:Zeile> — Vorher / Nachher / Begründung`) → Freigabe → nur das
  Freigegebene anwenden → Kurzbericht.

## Schritt 3 — Regeln beim Editieren

- Platzhalter dürfen ersetzt werden; vorhandener Fließtext nur an der beauftragten Stelle.
- Keine erfundenen Fakten oder Quellen; `\cite` nur mit existierendem Key.
- Neu erzeugte oder inhaltlich geänderte Blöcke mit `% @ai-generated JJJJ-MM-TT`; reine
  Kleinkorrekturen nicht.
- Geänderten Text gegen die KI-Stil-Checkliste prüfen.
- Kein Build.
