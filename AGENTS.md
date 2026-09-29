# AGENTS.md — Regeln für KI-Assistenten in diesem Repository

Diese Datei ist der werkzeugneutrale Kern. Claude Code liest sie über `CLAUDE.md` ein; GitHub Copilot,
Cursor, Codex und andere Assistenten lesen `AGENTS.md` direkt oder bekommen sie als Kontext mitgegeben.
Wer ein Werkzeug ohne Dateizugriff nutzt, kopiert diese Datei und die unten genannten Instructions an
den Anfang der Unterhaltung.

---

## Was dieses Repository ist

Die LaTeX-Quellen einer Abschlussarbeit. Der Text gehört dem Verfasser bzw. der Verfasserin. Die KI
ist Werkzeug für Entwürfe, Formalprüfung und Gegenlesen — nicht Autor. Jede Aussage im fertigen PDF
muss der Verfasser erklären und verteidigen können.

## Projektkontext (vom Verfasser auszufüllen)

> Diesen Abschnitt zu Beginn der Arbeit ausfüllen und laufend aktuell halten. Er ist die einzige
> Kontextquelle für `/thesis-editor` und die erste für alle anderen Commands. Was hier nicht steht,
> soll die KI erfragen statt raten.

- **Titel:** …
- **Art der Arbeit:** Arbeit mit Anforderungsanalyse | Arbeit mit bekannten Anforderungen
- **Worum es geht (3–5 Sätze):** …
- **Abgrenzung — was ausdrücklich nicht Teil der Arbeit ist:** …
- **Verbindliche Terminologie** (genau so schreiben; eine Sache, ein Begriff): …
- **Begriffe, die veraltet oder falsch sind und nicht mehr verwendet werden:** …
- **Weitere Quellen der Wahrheit:** Arbeitspakete in `Dokumentation/Arbeitspakete/AP_*.md`; ggf. Pfad zum Code-Repository: …
- **Vertraulich — nie in Text, Beispiele oder Prompts:** Firmen-/Kundennamen, interne Hostnamen und IPs,
  Zugangsdaten, echte Mess- oder Betriebsdaten: …

## Struktur

```
latex/                    alles, was zum PDF gehört; Build läuft in diesem Ordner
  main.tex                Präambel, Titelseite, Kapitelreihenfolge
  chapters/*.tex          ein File je Kapitel
  chapters/08.1_Abkuerzungsverzeichnis.tex   \DeclareAcronym-Definitionen (acro)
  literatur.bib           Quellen (IEEE über ieeetr-hm.bst)
  assets/                 Abbildungen; Diagrammquellen in assets/diagrams/*.md
Dokumentation/            Arbeitsdokumentation — nicht Teil des PDFs
  Arbeitspakete/          AP_*.md: Quelle der Wahrheit für alle Fachaussagen
.claude/instructions/     Prüfervorgaben, Schreibkonventionen, Prüfprompts

Pfade in \input, \includegraphics und \bibliography sind relativ zu latex/.
```

## Regeln (gelten immer, für jedes Werkzeug)

1. **Nichts erfinden.** Fakten, Zahlen, Messwerte, Versionsangaben, Funktionen des Systems und Quellen
   stammen aus der Nutzereingabe, aus `Dokumentation/Arbeitspakete/`, aus dem Code oder aus der bearbeiteten `.tex`-Datei.
   Fehlt etwas: nachfragen. Geplante, aber nie umgesetzte Funktionen aus frühen Planungsnotizen sind
   keine Fakten.
2. **Quellen nur mit existierendem Key** aus `latex/literatur.bib`. Keine Quelle einer Aussage zuordnen, die
   nicht nachweislich in ihr steht. `latex/literatur.bib` nur auf ausdrückliche Anfrage ändern; neue Einträge
   nur mit tatsächlich abgerufener URL.
3. **Form vs. Inhalt trennen.** Formale Korrekturen (LaTeX, Zitiersyntax, Abkürzungen, Satzbau bei
   gleicher Aussage) dürfen nach Freigabe direkt umgesetzt werden. Inhaltliche Änderungen (Aussage,
   Zahl, Bewertung, neue Argumente) werden vorgeschlagen, nicht eigenmächtig geschrieben. Im Zweifel
   gilt eine Änderung als inhaltlich.
4. **Vorschlag → Freigabe → Edit.** Bei allem, was nicht eindeutig und rein formal ist: erst ein
   nummeriertes Änderungsprotokoll zeigen, auf Freigabe warten, dann nur das Freigegebene anwenden.
5. **Vorhandenen Fließtext nicht ungefragt überschreiben.** Platzhalter (`TODO`, Stichpunkte) dürfen
   ersetzt werden.
6. **Abschnittsweise arbeiten.** Nie ein ganzes Kapitel in einem Zug erzeugen. Bei einem neuen Kapitel
   zuerst Gliederung und Rückfragen, dann ein einzelner Abschnitt zur Stil-Kalibrierung, dann Freigabe.
7. **Kein automatischer Build.** Nach Änderungen kein `latexmk`/`pdflatex`/`bibtex` und keine
   PDF-Prüfung — der Verfasser baut selbst im Editor. Ein paralleler Build greift gleichzeitig auf
   die Hilfsdateien (`latex/main.aux`, `latex/main.bbl`, …) zu und beschädigt sie. Nur bauen, wenn im aktuellen Prompt ausdrücklich
   verlangt.
8. **KI-Marker.** Neu erzeugte oder inhaltlich überarbeitete Blöcke erhalten eine Kommentarzeile
   `% @ai-generated JJJJ-MM-TT` (in Markdown `<!-- @ai-generated JJJJ-MM-TT -->`). Das macht später
   sichtbar, welche Stellen besonders gründlich selbst gelesen werden müssen.
9. **Vertrauliches bleibt draußen** (siehe Projektkontext). Beispiele und Illustrationen nutzen
   synthetische Werte.

## Verbindliche Instructions (vor dem Schreiben lesen)

- `.claude/instructions/vorgaben.md` — Vorgaben des Prüfers: Struktur, Umfang, Abbildungen, Zitierstil.
  Bei Widerspruch zu allgemeinen Gewohnheiten gilt diese Datei.
- `.claude/instructions/schreibkonventionen.md` — Stil, LaTeX-Konventionen und die Checkliste gegen
  erkennbaren KI-Stil. Jeder erzeugte Text wird vor der Ausgabe gegen diese Checkliste geprüft.
