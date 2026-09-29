---
description: Klärt vor der Umsetzung alle Unklarheiten per Rückfrage und arbeitet danach direkt weiter
argument-hint: [die eigentliche Aufgabe — leer = die Aufgabe aus der vorigen Nachricht]
---

Der Nutzer hat diesen Command hinter eine Aufgabe gehängt, weil er **ausdrücklich befragt werden
will**, bevor du etwas baust. Das ist kein Zusatzwunsch, sondern der Kern des Auftrags: Lieber eine
Runde Fragen zu viel als eine falsche Annahme im fertigen Code.

Aufgabe: $ARGUMENTS

Ist das leer, ist die Aufgabe aus der unmittelbar vorhergehenden Nachricht gemeint.

## Ablauf

**1. Erst recherchieren, dann fragen.** Bevor du irgendetwas fragst, lies nach, was das Repo schon
beantwortet: die betroffenen Dateien, `CLAUDE.md`, vorhandene Muster in Nachbarcode, bei Bedarf
`git log`/`git diff`. Frag gezielt und knapp — keine Rundgänge durch unbeteiligte Module. **Was im
Code eindeutig steht, wird nicht gefragt.** Eine Frage, deren Antwort du selbst hättest nachlesen
können, ist ein Fehler.

**2. Die echten Lücken herausarbeiten.** Übrig bleibt nur, was du nicht aus Code, Konventionen oder
gesundem Menschenverstand ableiten kannst. Typische Kandidaten:

- **Entscheidungen, die das Ergebnis verzweigen** — zwei vertretbare Umsetzungen, die zu spürbar
  unterschiedlichem Code führen.
- **Fehlender Kontext ausserhalb des Repos** — Ticketstand, Roadmap-Reihenfolge, fachliche Vorgaben,
  bereits verworfene Varianten. Darüber weisst du nichts; rate nicht.
- **Umfang und Grenzen** — gehört Randfall X dazu? Soll Bestehendes migriert werden? Ist die
  Änderung breaking und ist das gewollt?
- **Widersprüche** — die Aufgabe verlangt etwas, das dem Code, `CLAUDE.md` oder einer früheren
  Entscheidung zuwiderläuft. Das sprichst du an, statt es stillschweigend aufzulösen.

Nicht fragen: Naming, Dateipfade, Formatierung und andere Kleinigkeiten mit einer offensichtlichen
Hausvariante. Die entscheidest du selbst und sagst es beiläufig dazu.

**3. Fragen stellen.** Nutze das `AskUserQuestion`-Tool, nicht Freitext im Chat. Regeln:

- Höchstens vier Fragen pro Runde, die wichtigste zuerst.
- Jede Option nennt die Konsequenz, nicht nur die Bezeichnung: was konkret anders wird, wenn man sie
  wählt, inklusive Nachteil.
- Hast du eine fachliche Empfehlung, steht sie als **erste** Option mit „(Empfohlen)" im Label.
- Bei Layouts, Datenstrukturen oder konkurrierenden Code-Varianten nutzt du `preview` für eine
  Skizze, damit der Nutzer vergleichen kann.
- Eine zweite Runde ist erlaubt, wenn eine Antwort neue Verzweigungen aufmacht. Mehr als zwei Runden
  sind ein Zeichen, dass du zu kleinteilig fragst.

**4. Punkte nennen, die keine Frage sind.** Annahmen, die du triffst, ohne zu fragen, listest du in
ein bis zwei Sätzen vor oder nach der Fragerunde auf — damit der Nutzer widersprechen kann, ohne
dass daraus eine eigene Frage wird.

**5. Danach umsetzen.** Sobald die Antworten da sind, führst du die Aufgabe **vollständig aus** —
kein erneutes Nachfragen um Erlaubnis, kein Zwischenstand-Bericht statt Ergebnis. Die Antworten
gelten für diese Aufgabe verbindlich; ein bereits entschiedener Punkt wird nicht neu aufgerollt.
Tauchen mitten in der Umsetzung neue Unklarheiten auf, gilt weiter die Hausregel: erst alles
erledigen, was nicht davon abhängt, dann fragen.

**6. Am Ende.** Sag in ein, zwei Sätzen, was du gebaut hast und welche der geklärten Entscheidungen
dabei den Ausschlag gegeben haben. Alle projekteigenen Regeln — `CLAUDE.md`, Testkonventionen,
Formatierung — gelten unverändert.

## Sonderfall: nichts zu fragen

Ist die Aufgabe wirklich eindeutig, erfindest du keine Fragen, um beschäftigt zu wirken. Dann sagst
du in einem Satz, dass nichts offen ist, nennst deine Annahmen — und setzt um.
