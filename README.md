# Abschlussarbeit mit LaTeX und KI-Unterstützung — Template

Ein schlankes Startgerüst für eine Bachelor- oder Masterarbeit: LaTeX-Vorlage nach typischen
Prüfervorgaben und ein KI-Setup für [Claude Code](https://docs.claude.com/en/docs/claude-code/overview),
das sich auf andere Assistenten übertragen lässt. Es stammt aus einer Bachelorarbeit, die mit sehr gut
bewertet wurde; die Arbeit selbst ist nicht enthalten.

> **Das hier ist kein Ghostwriter.** Die KI schreibt Entwürfe, prüft Formalia und liest gegen. Den
> Text verantwortest du — jede Aussage im PDF musst du im Vortrag erklären können.

---

## Voraussetzungen

**Software**

- [VS Code](https://code.visualstudio.com/) und [Git](https://git-scm.com/)
- eine LaTeX-Distribution mit `latexmk` (Installation siehe Schnellstart)
- für die KI-Commands: [Claude Code](https://docs.claude.com/en/docs/claude-code/overview) mit einem
  kostenpflichtigen Claude-Abo (Pro/Max) oder API-Guthaben. GitHub Copilot ist für Studierende über
  [GitHub Education](https://education.github.com/) kostenlos und liest `AGENTS.md` ebenfalls.

**Vorwissen**

- **Git:** committen, Diffs lesen, einzelne Stellen stagen, Branches anlegen. Der Arbeitsablauf
  unten baut darauf auf.
- **LaTeX:** `\input`, `\cite`, `\label`/`\autoref`, Abbildungen und Tabellen, BibTeX-Einträge
  anlegen — und vor allem Fehlermeldungen im Build-Log lesen. Die KI hilft dabei, ersetzt es aber nicht.
- **VS Code:** Erweiterungen installieren, das integrierte Terminal nutzen.
- **Claude Code:** Slash-Commands aufrufen und Berechtigungsabfragen beantworten. Beim ersten Start
  fragt Claude Code, ob es den Einstellungen des Projekts vertrauen soll; was die KI ohne Rückfrage
  darf, regelt `.claude/settings.json`.

## Schnellstart

1. Repository übernehmen („Use this template" auf GitHub oder klonen).
2. LaTeX installieren:
   - **Windows:** [MiKTeX](https://miktex.org/) und zusätzlich [Strawberry Perl](https://strawberryperl.com/) —
     MiKTeX bringt kein Perl mit, `latexmk` braucht es aber. In der MiKTeX Console unter
     *Settings* „Fehlende Pakete installieren" auf **Immer** stellen, sonst hängt oder scheitert der
     erste Build an Paketen wie `acro`.
   - **macOS/Linux:** [TeX Live](https://tug.org/texlive/) bzw. MacTeX, am einfachsten vollständig
     (`scheme-full`); Perl ist dort vorhanden.
3. Ordner in VS Code öffnen und die empfohlenen Erweiterungen installieren (VS Code fragt beim ersten
   Öffnen nach, siehe unten). Speichern einer `.tex`-Datei baut `latex/main.pdf`.
   Ohne Editor: `latexmk -cd -pdf latex/main.tex`.
   Die mitgelieferte `latex/main.pdf` ist nur eine Vorschau der leeren Vorlage. Nach dem Übernehmen
   aus Git nehmen, sonst erzeugt jeder Build einen Diff:
   `git rm --cached latex/main.pdf` und `latex/main.pdf` in die `.gitignore` eintragen.
4. In `latex/main.tex` Titel und Autor (`\thesistitel`, `\thesisautor`) und die Titelseite anpassen.
5. `.claude/instructions/vorgaben.md` mit den Vorgaben **deines** Prüfers abgleichen — die Datei ist eine Vorlage.
6. Den Abschnitt „Projektkontext" in `AGENTS.md` ausfüllen.

Alles, was zum PDF gehört, liegt in `latex/`. Der Build läuft in diesem Ordner (LaTeX Workshop baut
im Ordner der Hauptdatei, `latexmk -cd` wechselt dorthin), damit die `\input`-Pfade stimmen und BibTeX
`literatur.bib` und `ieeetr-hm.bst` direkt findet. Die Hilfsdateien (`.aux`, `.log`, …) entstehen neben
`main.tex` und in `latex/chapters/`; `.vscode/settings.json` blendet sie im Explorer aus, `.gitignore`
hält sie aus Git heraus.

### Diagramme

Jede Abbildung liegt als Markdown-Datei mit einem ` ```mermaid `-Block in `latex/assets/diagrams/` — lesbar
im Git-Diff, in der Markdown-Vorschau und für die KI. Die Dateien erklären zusätzlich die
Diagrammregeln der Vorgaben (Pfeilsyntax im Sequenzdiagramm, DIN 66001 im Programmablaufplan).

Zum Rendern den Mermaid-Block in [mermaid.live](https://mermaid.live) einfügen, als PNG exportieren
und als `<name>.png` neben die `<name>.md` legen. Die Schrift im Diagramm soll etwa der
Dokumentschrift entsprechen: lieber in hoher Auflösung exportieren und in LaTeX mit
`width=0.6\textwidth` bis `0.9\textwidth` einbinden, dann im PDF vergleichen. Mermaid ist ein
Angebot, keine Pflicht — Abbildungen aus draw.io, PowerPoint oder Screenshots (über `\screenshot`)
funktionieren genauso; die Diagrammregeln aus den Vorgaben gelten für alle.

### VS-Code-Erweiterungen

| Erweiterung                                                                                                      | Wofür                                                                                                                    |
| ---------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop)                     | Build mit `latexmk` beim Speichern, PDF-Vorschau im Tab, SyncTeX (Strg+Klick springt zwischen PDF und Quelltext)         |
| [Claude Code](https://marketplace.visualstudio.com/items?itemName=anthropic.claude-code)                          | KI-Assistent im Editor; nutzt `CLAUDE.md` und die Commands aus `.claude/`                                              |
| GitHub Copilot                                                                                                   | in VS Code eingebaut, keine Installation nötig; KI-Chat und Vervollständigung als zweite Meinung neben Claude Code      |
| [Explorer Exclude Manager](https://marketplace.visualstudio.com/items?itemName=madcatpx.explorer-exclude-manager) | Dateien und Ordner (z. B. `.claude/`, `Dokumentation/Arbeitspakete/`) per Klick im Explorer aus- und wieder einblenden |

Die Empfehlungen stehen in `.vscode/extensions.json`, die zugehörigen Einstellungen in
`.vscode/settings.json` (ausgeblendete LaTeX-Hilfsdateien, Claude Code im Panel).
Die verwendeten Erweiterungen samt Version gehören in das Unterkapitel „Verwendete Entwicklungs- und
Hilfsmittel".

---

## Struktur

```
latex/                      alles, was zum PDF gehört
  main.tex                  Präambel, Titelseite, Kapitelreihenfolge
  chapters/                 ein File je Kapitel, mit Hinweisen, was hineingehört
  literatur.bib             Beispieleinträge: RFC, offizielle Doku, Buch
  ieeetr-hm.bst             IEEE-Stil: Titel in Anführungszeichen UND kursiv, Groß-/Kleinschreibung bleibt
  assets/hm-logo.png        Logo der Titelseite (für eine andere Hochschule ersetzen oder löschen)
  assets/diagrams/          Diagramme: Mermaid-Quelle (.md) und gerenderte PNGs
Dokumentation/              Arbeitsdokumentation, nicht im PDF. Weitere Unterordner für Notizen, Protokolle, Recherchen …
  Arbeitspakete/AP_Vorlage.md  Vorlage für Arbeitspakete (Quelle der Wahrheit)
AGENTS.md                   Regeln + Projektkontext für jede KI
CLAUDE.md                   lädt AGENTS.md und die Instructions in Claude Code
.claude/commands/           Slash-Commands
.claude/instructions/       Prüfervorgaben, Schreibkonventionen, Prüfprompts
.claude/settings.json       KI schreibt in latex/ und Dokumentation/; literatur.bib nur nach Rückfrage, .bst nie
.vscode/                    empfohlene Erweiterungen und Editor-Einstellungen
```

---

## KI-Aufbau

| Command                   | Wofür                                                        | Darf Inhalt ändern?                              |
| ------------------------- | ------------------------------------------------------------- | ------------------------------------------------- |
| `/dokumentator AP3: …` | Rohnotizen strukturiert ins Arbeitspaket schreiben            | nur Notizen                                       |
| `/kapitelschreiber`     | einen Abschnitt als LaTeX-Entwurf ins Kapitel schreiben       | ja, auf Basis der Notizen                         |
| `/bachelor-adjuster`    | Stil, Struktur, Zitation, Abkürzungen prüfen                | **nein** — nur formale Edits nach Freigabe |
| `/thesis-editor`        | gezielte Änderungen, fragt bei jeder Unklarheit              | ja                                                |
| `/grill-me <Aufgabe>`   | vor einer Aufgabe alle offenen Punkte abfragen, dann umsetzen | wie die Aufgabe selbst                            |

### Befragen lassen mit `/grill-me`

`/grill-me` ist kein eigener Schreib-Agent. Der Command wird **vor eine Aufgabe gesetzt**, wenn man
ausdrücklich ausgefragt werden will, bevor die KI etwas schreibt:

1. Die KI liest zuerst nach, was Repository, `AGENTS.md` und Arbeitspakete schon beantworten. Was dort
   eindeutig steht, fragt sie nicht.
2. Sie fragt nur die echten Lücken ab: Entscheidungen, bei denen zwei Varianten zu spürbar anderem Text
   führen, Wissen außerhalb des Repositorys (Absprachen mit dem Betreuer, verworfene Ideen), Umfang und
   Widersprüche. Es sind höchstens vier Fragen pro Runde. Jede Option nennt ihre Konsequenz, eine
   Empfehlung steht an erster Stelle.
3. Annahmen, die keine eigene Frage wert sind, nennt sie in ein bis zwei Sätzen, damit man
   widersprechen kann.
4. Danach setzt sie die Aufgabe vollständig um, ohne erneut um Erlaubnis zu fragen. Ist nichts offen,
   sagt sie das und legt direkt los.

**Aufruf:** `/grill-me <Aufgabe>` oder ohne Argument direkt nach der Nachricht, in der die Aufgabe steht.
Soll ein Schreib-Command die Regeln liefern, nennt man ihn in der Aufgabe, etwa
`/grill-me Abschnitt 5.2 zum Lasttest nach .claude/commands/kapitelschreiber.md entwerfen`.

**Wann es sich lohnt:** bei einem neuen Kapitel oder dessen Gliederung, bei der Bewertung in
„Zusammenfassung und Ausblick", bei größeren Umbauten und immer dann, wenn man selbst noch nicht genau
weiß, was man will. Bei eindeutigen Kleinkorrekturen bremst es nur.

**Ohne Claude Code:** Copilot, Cursor und Codex lesen `AGENTS.md`. Die Dateien in `.claude/commands/`
sind normale Markdown-Prompts — Inhalt kopieren und `$ARGUMENTS` durch die eigene Eingabe ersetzen.
In einem Chat ohne Dateizugriff `AGENTS.md`, `vorgaben.md` und `schreibkonventionen.md` mitgeben.

## Ohne Git geht es nicht

**Arbeite von Anfang an mit Git.** Erst dadurch lässt sich mit KI vernünftig arbeiten: Jede Änderung
der KI wird sichtbar, du nimmst sie gezielt an oder verwirfst sie, überarbeitest sie und hältst den
Stand als Version fest. Ohne Versionierung überschreibt eine KI-Session unbemerkt einen Absatz, den du
schon verbessert hattest — und es gibt keinen Weg zurück.

- **Vor jeder KI-Session committen.** Dann ist genau das, was die KI geändert hat, der Unterschied
  zum letzten Commit — nichts vermischt sich mit eigenen Änderungen.
- **Jede Änderung im Diff prüfen** (in VS Code: Quellcodeverwaltung, Datei anklicken). Du siehst
  Satz für Satz, was hinzugekommen, entfernt oder umformuliert wurde.
- **Annehmen heißt stagen.** Übernimm gute Teile einzeln (Stage Selected Ranges), verwirf den Rest
  (Discard Changes) und überarbeite den Text selbst, bevor du committest. Die KI darf in diesem
  Template nicht selbst stagen oder committen (`.claude/settings.json`) — die Entscheidung bleibt bei dir.
- **Kleine Commits mit klarer Nachricht**, etwa einer je Abschnitt: „Kap. 5.2 Lasttest: Entwurf
  überarbeitet". So lässt sich später jede Passage zu ihrem Entstehungsschritt zurückverfolgen.
- **Größere Umbauten auf einem eigenen Branch.** Gefällt das Ergebnis nicht, wird der Branch
  verworfen und der alte Stand ist unverändert da.
- **Regelmäßig pushen** (GitHub, GitLab, Hochschul-Git, Forgejo). Das ist zugleich die Sicherung der Arbeit.

Die Historie belegt außerdem, wie die Arbeit entstanden ist — hilfreich, wenn im Vortrag oder bei
Rückfragen die eigene Leistung neben der KI-Unterstützung erklärt werden soll.

## Ablauf

1. Während der Entwicklung Entscheidungen, Probleme und Messwerte mit `/dokumentator` festhalten.
2. Kapitel **abschnittsweise** mit `/kapitelschreiber` entwerfen — vorher committen.
3. **Selbst lesen und umschreiben** — jeden Entwurf, Satz für Satz im Diff, Zahlen gegen Code und
   Notizen. Erst dann stagen und committen.
4. Formal prüfen mit `/bachelor-adjuster`.
5. Mit einer zweiten KI gegenchecken ([Prompt](.claude/instructions/pruefprompts/quercheck_zweite_ki.md)).
6. Vor der Abgabe die [Prüfprompts](.claude/instructions/pruefprompts/abgabe.md) und die
   [Belegdeckung](.claude/instructions/pruefprompts/quellendeckung.md) durchlaufen, dann das fertige
   PDF noch einmal selbst lesen.

---

## Was gut funktioniert hat

- **Eine Quelle der Wahrheit unter dem Text.** Die Arbeitspakete halten fest, was tatsächlich gebaut
  und gemessen wurde. Die KI schreibt gegen diese Notizen statt aus Allgemeinwissen, und man selbst
  kann jede Aussage dort nachprüfen.
- **Die Vorgaben des Prüfers als Instruction.** Jede Session prüft gegen dieselben Regeln. Die
  Dokumentqualität zählt ungefähr so viel wie das technische Ergebnis.
- **Getrennte Rollen.** Ein Command, der nur formal prüfen darf, kann keine Aussage verfälschen.
  Änderungen kommen als nummeriertes Protokoll und werden einzeln freigegeben.
- **Abschnittsweise schreiben.** Erst ein Abschnitt, dann Feedback, dann der nächste.
- **Prüfprompts in frischen Sessions mit Belegpflicht** (Datei:Zeile, wörtliches Quellenzitat). Am
  wertvollsten: die Durchgängigkeit Anforderung → Konzept → Implementierung → Test → Bewertung.
- **Entscheidungen im Projektkontext festhalten** („Funktion X wurde nie umgesetzt"), damit keine
  Session sie aus alten Planungsnotizen zurückholt.
- **Kein Build durch die KI** und **`% @ai-generated`-Marker** an erzeugten Stellen.

## Was man vermeiden sollte

- **Erkennbarer KI-Stil** — bei anderen Arbeiten am deutlichsten negativ aufgefallen: Floskel-Einstiege,
  leere Dreiklänge („robust, skalierbar und flexibel"), Listen statt Argumentation, „Zusammenfassend
  lässt sich festhalten", „deutlich" ohne Zahl, Fettdruck im Fließtext. Vollständige Liste in
  [`schreibkonventionen.md`](.claude/instructions/schreibkonventionen.md#checkliste-gegen-erkennbaren-ki-stil).
- **Übernehmen, ohne zu lesen.** Immer alles selbst durchlesen und prüfen. Was du nicht erklären
  kannst, gehört nicht in deine Arbeit.
- **Nur einer KI vertrauen.** Bei Gelegenheit mit einer zweiten gegenchecken — deren Vorschläge sind
  aber genauso ungeprüft.
- **Ganze Kapitel generieren lassen.** Lang, gleichförmig, und niemand prüft 30 Seiten am Stück gründlich.
- **Quellen nicht selbst öffnen.** Modelle ordnen Quellen nach Plausibilität zu und erfinden
  gelegentlich Kapitelnummern oder Titel.
- **Fakten ergänzen lassen.** Ein „sinnvoll ergänzter" Messwert ist erfunden. Fehlt etwas: `TODO`.
- **Vertrauliches in Prompts** (Firmennamen, interne Server, Zugangsdaten, echte Betriebsdaten).
- **KI-Nutzung verschweigen.** Das Unterkapitel „Verwendete Entwicklungs- und Hilfsmittel" in
  `latex/chapters/04_Konzipierung_der_Loesung.tex` nennt alle KI-Werkzeuge mit Einsatzzweck; die
  Selbständigkeitserklärung verweist darauf. Nur angeben, was tatsächlich genutzt wurde.

---

## Lizenz

Alle Inhalte dieses Templates — Code, Konfiguration, Texte und Prompts — stehen unter
[CC0 1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/deed.de) (Public Domain).
Du darfst alles ohne Bedingungen nutzen, ändern und weitergeben, auch ohne Namensnennung, und diesen
Abschnitt in deiner Kopie löschen. Über einen Link auf dieses Repository freue ich mich trotzdem.

Ausgenommen sind:

- `latex/ieeetr-hm.bst` — umbenannte Ableitung von `ieeetr.bst` (© Howard Trickey, Oren Patashnik);
  es gilt die Lizenz im Dateikopf (Weitergabe erlaubt, geänderte Fassungen nur unter neuem Namen).
- `latex/assets/hm-logo.png` — Zeichen der Hochschule München, fällt nicht unter CC0.

`vorgaben.md` ist eine allgemeine Zusammenfassung — verbindlich sind die Vorgaben deines Prüfers.
