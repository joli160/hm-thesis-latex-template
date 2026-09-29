# Prüfprompts vor der Abgabe

Grundlage aller Prüfungen: [`../vorgaben.md`](../vorgaben.md). Die Prompts sind **read-only**
formuliert: erst messen und berichten, dann auf Freigabe warten, dann nur das Freigegebene ändern.

## So benutzen

- **Je Prompt eine frische Session.** Sonst färbt der Kontext des vorigen Durchgangs die Bewertung.
- **Reihenfolge:** A → B → C → D → E → G → F. A liefert die Messgrundlage; E misst den Umfang erst nach
  inhaltlichen Änderungen; G läuft nach C und D, weil beide die Verzeichnisse verändern.
- **Effort `high`.** `max` bringt bei diesen Prüfungen kaum etwas außer Laufzeit.
- **Web-Zugriff** ist für D Pflicht.
- **Ergebnisse nicht wiederverwenden.** Ein Prüfbericht von letzter Woche ist nach den Korrekturen
  veraltet. Wer ihn als Wissensbasis in den nächsten Durchgang gibt, bekommt erledigte Punkte erneut
  gemeldet. Jeder Durchgang misst selbst.
- Bei knapper Zeit sind **A, B, G, F Pflicht**; C, D, E in dieser Rangfolge kürzen.

## Gemeinsame Regeln (in jedem Prompt enthalten)

```
- Nichts erfinden: keine Seitenzahl, Zeilennummer, Logmeldung, URL, RFC-Nummer, kein Quellenzitat.
  Was nicht geprüft wurde, heißt "nicht geprüft".
- Bis zur Freigabe ÄNDERE NICHTS. Inhaltliche Aussagen nie ohne Rückfrage umformulieren.
- Ein leerer Befund ist ein gültiges Ergebnis. Konstruiere keine Probleme.
- Grenzfälle als Grenzfälle kennzeichnen und begründen, nicht als Verstoß.
- Build: latexmk -cd -pdf latex/main.tex im Wurzelverzeichnis. Maßgeblich ist latex/main.pdf.
```

---

## Prompt A — Build, PDF-Qualität, Referenz-Integrität

```
Prüfe Build und PDF-Qualität meiner Abschlussarbeit. Lies zuerst .claude/instructions/vorgaben.md,
Abschnitte 1, 3.5, 3.12 und 6.

SCHRITT 1 — Build: latexmk -cd -pdf latex/main.tex. Berichte Exit-Code und ob BibTeX fehlerfrei lief
(latex/main.blg). Prüfe latex/main.bbl gegen 0 Byte — ein leeres .bbl bedeutet unaufgelöste Zitate
ohne sichtbaren Fehler.

SCHRITT 2 — Referenzen (Soll überall 0), gemessen an latex/main.log und latex/main.aux:
undefinierte Referenzen, undefinierte Zitate, mehrfach definierte Labels — je einzeln. Quellen im
Verzeichnis ohne Zitat im Text, Keys ohne Verzeichniseintrag. Suche im PDF-Text nach "??" und "[?]".

SCHRITT 3 — Navigation: Inhaltsverzeichnis klickbar? Bookmarks vorhanden, nummeriert, aufgeklappt?
pdftitle/pdfauthor gefüllt, Umlaute korrekt? Alle URLs im Quellenverzeichnis klickbar?

SCHRITT 4 — Anhang: Jedes \label aus dem Anhang mindestens einmal aus dem Fließtext referenziert?

SCHRITT 5 — Satz: Overfull hbox/vbox mit Betrag und Seite; ragt im Fließtext sichtbar Text über den
Rand? Zurückgebliebene Platzhalter (TODO,
FIXME, "Platzhalter") — echte Platzhalter von Fallback-Makros unterscheiden.

AUSGABE: Checkliste Prüfpunkt | Soll | Ist (Fundstelle) | OK/FEHLER | Fix. Danach Kennzahlen:
Seiten, Warnungen, Labels, Zitate, Bookmarks, Overfull. Dann Korrekturvorschlag und WARTEN.
[Gemeinsame Regeln]
```

## Prompt B — Anforderungs-Durchgängigkeit (der wichtigste Prüfpunkt)

```
Lies .claude/instructions/vorgaben.md Abschnitt 3.7.

1. Extrahiere ALLE dokumentierten Anforderungen mit IDs (Kapitel Anforderungsanalyse bzw. 1.2).
2. Prüfe je Anforderung: in der Konzipierung aufgegriffen? in der Implementierung umgesetzt? im
   Testkapitel getestet oder der Nicht-Test begründet? in der Zusammenfassung bewertet?
3. Gegenrichtung: Inhalte in Implementierung/Tests, die KEINER Anforderung zuzuordnen sind, und
   Bewertungsaussagen in der Zusammenfassung ohne Anforderungsbezug.

AUSGABE: Matrix ID | Konzept | Implementierung | Test | Bewertung — jeweils Datei:Zeile oder FEHLT.
Dann gesondert: (a) Anforderungen ohne Test, (b) verwaiste Inhalte, (c) Bewertungen ohne Bezug.
[Gemeinsame Regeln]
```

## Prompt C — Abbildungen

```
Lies .claude/instructions/vorgaben.md Kapitel 4.

1. Je Abbildung: Nummer + Caption vorhanden? mindestens ein \autoref im Text?
2. Schriftgrößen RECHNEN, nicht schätzen: aus Bildbreite in Pixel, Einbindungsbreite im LaTeX und
   Schriftgröße im Bild die effektive Punktgröße im PDF bestimmen; mit der Grundschrift vergleichen.
3. Diagrammsyntax: Blockdiagramme mit Protokoll und (S)/(C) an Netzwerkpfeilen; Sequenzdiagramme mit
   korrekten synchron/asynchron/Antwort-Pfeilen; Programmablaufpläne mit Start/Stop, keine offenen
   Enden, Rauten mit genau zwei Ausgängen.

AUSGABE: Tabelle je Abbildung mit Befund und Fix.
[Gemeinsame Regeln]
```

## Prompt D — Quellen: Format und Vollständigkeit

```
Lies .claude/instructions/vorgaben.md Kapitel 5 und latex/literatur.bib.

1. Format je Eintrag gegen 5.1 (Autor/Organisation, Titel, Dokumentdatum, URL, Zugriffsdatum).
2. Zugriffsdaten einheitlich und nah am Abgabetermin?
3. Standards, Protokolle, Sprachen und Datenformate mit Primärquelle belegt (5.3)?
4. Jede URL aufrufen: 404/403/Umleitung auf anderen Inhalt melden.
Für die inhaltliche Belegdeckung gibt es den eigenen Prompt quellendeckung.md.
[Gemeinsame Regeln]
```

## Prompt E — Struktur, Umfang, Sprachstil

```
Lies .claude/instructions/vorgaben.md Abschnitt 3 und .claude/instructions/schreibkonventionen.md.

1. Gliederung gegen die Soll-Struktur (3.2) inkl. Pflicht-Unterkapitel am Ende der Konzipierung.
2. Umfang aus dem eigenen Build: Seiten ohne Anhang, Anteil des Hauptteils, Verteilung je Kapitel.
3. Gliederungstiefe (3.3), auch \paragraph-Überschriften.
4. Hilfsmittel-Kapitel: Sind ALLE KI-Werkzeuge mit Einsatzzweck genannt? Deckt es die Aussage der
   Erklärung zur Selbständigkeit?
5. Sprachstil in allen Kapiteln inkl. Kurzfassung/Abstract: Umgangssprache, Ich-Form, Werbesprache,
   unbelegte Steigerungen (gibt es einen Messwert im Testkapitel?), inkonsistente Terminologie und
   ALLE Muster der Checkliste gegen erkennbaren KI-Stil. Maximal die 30 gravierendsten Fundstellen:
   Datei:Zeile | Zitat | Problem | Vorschlag. Stiländerungen entscheide ich pro Fundstelle.
[Gemeinsame Regeln]
```

## Prompt G — Vollständigkeit der Verzeichnisse

```
1. Abkürzungen, Richtung A: Jede im Text verwendete Abkürzung deklariert und bei Erstnennung
   ausgeschrieben? Richtung B: Einträge, die nie verwendet werden oder nicht ins Verzeichnis gehören
   (Produktnamen, Code-Bezeichner)?
2. Abbildungs- und Tabellenverzeichnis: jeder Eintrag vorhanden, Kurzcaptions sinnvoll?
3. Inhalts- und Quellenverzeichnis vollständig und klickbar?
[Gemeinsame Regeln]
```

## Prompt F — Abgabe-Freigabe (zuletzt)

```
A–E und G sind gelaufen, die freigegebenen Korrekturen sind eingearbeitet. Deine Aufgabe ist NICHT,
inhaltlich neu zu prüfen, sondern die Freigabe.

1. Frischer Build; Kennzahlen aus Prompt A erneut messen. Umfang im Korridor?
2. Titelseite vollständig, alle Pflichtteile in der richtigen Reihenfolge, keine Platzhalter.
3. Widersprüche, die durch Korrekturen entstanden sein können: Hilfsmittel-Kapitel vs. Testkapitel,
   Kurzfassung vs. Abstract vs. Zusammenfassung, Erklärung zur Selbständigkeit vs. Hilfsmittel-Kapitel.
   Stichprobe von 15 \autoref-Verweisen: zeigt der Verweis sachlich auf das gemeinte Ziel?
4. Im Text genannte Zahlen gegen Tabellen und Abbildungen.

AUSGABE: Ampelliste ROT (Blocker) | GELB (sichtbar, < 30 min) | GRÜN. Am Ende EIN Satz:
abgabefähig ja/nein — und falls nein, welcher Punkt entgegensteht.
[Gemeinsame Regeln]
```
