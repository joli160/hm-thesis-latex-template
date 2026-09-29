# Schreibkonventionen

## Sprache und Stil

- Akademischer deutscher Fließtext, sachlich, in der dritten Person oder im Passiv
  („Der Worker entnimmt …", „Es wurde festgelegt …") statt „ich" oder „wir".
- Keine Umgangssprache („funktioniert super", „einfach", „natürlich", „nervig") und keine Wertungen
  ohne Beleg („sehr elegant", „deutlich schneller" ohne Messwert).
- Argumentieren statt aufzählen: Listen und Tabellen nur, wo der Inhalt tatsächlich listenförmig ist
  (Anforderungen, Versionsstände, Vergleich von Alternativen).
- Eine Sache, ein Begriff — die Terminologie aus dem Projektkontext in `AGENTS.md` gilt verbindlich.
- Zielpublikum: technisch gebildet, aber fachfremd. Grundbegriffe knapp einführen.
- Englische Fachbegriffe (Polling, Thread, Callback) normal setzen, nicht kursiv.

## Abkürzungen

- Über das `acro`-Paket: `\ac{key}` im Text, Definition in `latex/chapters/08.1_Abkuerzungsverzeichnis.tex`.
- Erstnennung ausgeschrieben mit Kurzform in Klammern, danach nur die Kurzform. Maßgeblich ist die
  Lesereihenfolge; Kurzfassung und Abstract führen eigenständig ein.
- Nicht ins Verzeichnis: Produkt- und Frameworknamen, SI-Einheiten, Code-Bezeichner.

## LaTeX

- `\texttt{}` nur für echte Code-Bezeichner; Unterstriche escapen (`\texttt{run\_id}`).
- Verweise immer mit `\autoref{fig:…}` / `\autoref{tab:…}` / `\autoref{sec:…}`, nie „siehe Abbildung 3".
- Label-Präfixe: `cha:`, `sec:`, `fig:`, `tab:`.
- Diagramme als Mermaid-Quelle in `latex/assets/diagrams/<name>.md`, als `<name>.png` daneben
  (Export z. B. über mermaid.live), eingebunden mit `\includegraphics`.
- Screenshots über `\screenshot` (grauer Rahmen).
- Abbildungen, die am Text haften sollen, mit `[H]`.
- Zitate: `\cite{key}` vor dem Satzzeichen; nur existierende Keys.

## Kapitelgrenzen

- **Grundlagen:** schlank, am Ende zuschneiden. Nicht in der Konzipierung wiederholen — dort per
  `\autoref` zurückverweisen.
- **Konzipierung:** WARUM und WAS (Entscheidungen, Alternativen, Bezug zu Anforderungs-IDs).
- **Implementierung:** WIE.
- **Tests:** Nachweis je Anforderung.
- **Zusammenfassung:** Bewertung nur gegen die dokumentierten Anforderungen.

---

## Checkliste gegen erkennbaren KI-Stil

Jeder von einer KI erzeugte oder überarbeitete Absatz wird vor der Ausgabe gegen diese Liste geprüft —
von der KI selbst **und danach vom Verfasser beim Lesen**. Gutachter erkennen diese Muster schnell,
und ein Text, der nach Modell klingt, verliert Vertrauen, auch wenn er fachlich stimmt.

| Muster | Beispiel | Besser |
|--------|----------|--------|
| Floskel-Einstieg | „In der heutigen, zunehmend digitalisierten Welt spielt … eine zentrale Rolle." | Direkt mit der Sache beginnen. |
| Leere Dreiklänge | „robust, skalierbar und flexibel" | Die eine Eigenschaft nennen, die belegt ist — mit Beleg. |
| „Nicht nur …, sondern auch" als Dauerkonstruktion | „Das System ist nicht nur schnell, sondern auch zuverlässig." | Zwei einfache Aussagen, jede begründet. |
| Aufzählung statt Argument | Fünf Spiegelstriche, wo ein Absatz eine Begründungskette braucht | Fließtext mit „weil", „dadurch", „daher". |
| Zusammenfassende Schlusssätze | „Zusammenfassend lässt sich festhalten, dass …" am Ende jedes Absatzes | Streichen. Der Absatz endet mit seiner letzten Aussage. |
| Selbstbezogene Ankündigungen | „Im Folgenden wird detailliert erläutert, wie …" | Nur am Kapitelanfang, und dann knapp. |
| Unbelegte Steigerungen | „deutlich", „erheblich", „signifikant" ohne Zahl | Messwert nennen oder Wort streichen. |
| Gedankenstrich- und Doppelpunkt-Kaskaden | „Das Ergebnis: ein System — schnell, sicher — das …" | Normaler Satzbau. |
| Fettdruck im Fließtext | „Das **zentrale** Element ist …" | Kein Fettdruck im Fließtext. |
| Übersetzte Anglizismen | „Dies macht Sinn", „am Ende des Tages" | „Das ist sinnvoll", streichen. |
| Absicherungsrhetorik | „kann potenziell unter Umständen dazu beitragen" | Klare Aussage oder offen benannte Einschränkung. |
| Gleichförmige Absatzlänge und -struktur | Jeder Absatz: Behauptung, drei Punkte, Fazit | Länge und Aufbau folgen dem Inhalt. |

**Wichtig:** Ein Wort, das eine Einschränkung präzisiert („lediglich", „bewusst begrenzt"), trägt
Bedeutung und ist kein Füllwort. Nur streichen, was wirklich leer ist.
