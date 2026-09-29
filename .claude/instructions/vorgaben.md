# Vorgaben des Prüfers

> **Diese Datei ist eine Vorlage.** Sie fasst Vorgaben zusammen, wie sie an technischen Fakultäten
> üblich sind, und diente in der Referenzarbeit als verbindliche Instruction. Ersetze bzw. ergänze sie
> mit den **schriftlichen Vorgaben deines eigenen Prüfers** — möglichst vollständig und in derselben
> Gliederung, damit die Prüfprompts ihre Abschnittsnummern wiederfinden. Wo dein Prüfer etwas anderes
> verlangt, gilt immer dein Prüfer.
>
> Je genauer diese Datei ist, desto mehr nützen die Commands: Jede Regel, die hier steht, kann die KI
> prüfen. Jede Regel, die fehlt, prüft sie nicht.

---

## 1 Allgemeines

- Die Arbeit ist ein wissenschaftliches Dokument: sachliche Sprache, keine Umgangssprache, keine
  Wertungen ohne Beleg.
- Abgabe als PDF. Alle internen und externen Hyperlinks müssen funktionieren und auf die richtige
  Stelle zeigen.

## 2 Exposé und Kategorie der Arbeit

- Zu Beginn ein schriftliches Exposé (1–2 Seiten) mit Kontext, Erwartungen und **Abgrenzung**.
- Kategorie früh festlegen:
  - **Arbeit mit bekannten Anforderungen** — Anforderungen stehen in „1.2 Anforderungen und Abgrenzung",
    kein eigenes Kapitel Anforderungsanalyse.
  - **Arbeit mit Anforderungsanalyse** — eigenes Kapitel „Anforderungsanalyse"; die Abgrenzung steht in
    „1.1 Motivation, Ziel und Abgrenzung der Arbeit".

## 3 Umfang, Struktur und Aufbau

### 3.1 Umfang und Satzspiegel

- Bachelorarbeit ca. 40–60 Seiten, Masterarbeit ca. 60–80 Seiten (jeweils ohne Anhang).
- Schriftgröße 10–12 pt, Zeilenabstand 1,2- bis 1,4-fach.

### 3.2 Struktur (Variante mit Anforderungsanalyse)

```
Titelblatt, Kurzfassung, Abstract, Inhaltsverzeichnis
1 Einleitung
  1.1 Motivation, Ziel und Abgrenzung der Arbeit
  1.2 Verwandte Arbeiten
  1.3 Inhaltlicher Aufbau der Arbeit
2 Grundlagen
3 Anforderungsanalyse
4 Konzipierung der Lösung
  4.1 Konzept und System
  4.x …
  4.y Verwendete Hard- und/oder Software
  4.z Verwendete Entwicklungs- und Hilfsmittel
5 Implementierung
6 Tests und Testergebnisse
7 Zusammenfassung und Ausblick
8 Verzeichnisse (Abkürzungen, Quellen, optional Abbildungen/Tabellen/Listings)
9 Erklärung zur Selbständigkeit
10 Danksagung (optional)
11 Anhang (optional)
```

Bei bekannten Anforderungen entfällt Kapitel 3; die Nummern verschieben sich entsprechend.
Abweichungen früh mit dem Betreuer abstimmen.

### 3.3 Gliederungstiefe

Maximal drei Überschriftenebenen, in Ausnahmefällen vier. Keine weitere Untergliederung — auch
nicht durch nicht-nummerierte Zwischenüberschriften (`\paragraph`).

### 3.4 Kurzfassung und Abstract

Ca. eine halbe Seite; Abstract ist die englische Fassung. Beide identisch mit den Angaben im
Abgabeformular der Hochschule.

### 3.5 Inhaltsverzeichnis und PDF-Navigation

Klickbares Inhaltsverzeichnis und eine Bookmarkstruktur im PDF.

### 3.7 Anforderungen als roter Faden

Konzipierung und Implementierung müssen sich aus den dokumentierten Anforderungen ergeben. Tests und
die abschließende Bewertung der Zielerreichung stützen sich **ausschließlich** auf diese Anforderungen.
Das ist die häufigste Schwäche von Abschlussarbeiten.

### 3.8 Verwandte Arbeiten

Literatur- und Internetrecherche; Suchmaschinen, Suchbegriffe und relevante Treffer dokumentieren.

### 3.10 Grundlagen

Nur, was zum Verständnis nötig ist. Empfehlung: erst den Hauptteil schreiben, dann die Grundlagen
passend zuschneiden.

### 3.11 Hauptteil

Die Kapitel zwischen Grundlagen und Zusammenfassung machen ca. zwei Drittel des Umfangs aus. Am Ende
der Konzipierung stehen die Unterkapitel „Verwendete Hard- und/oder Software" und „Verwendete
Entwicklungs- und Hilfsmittel" — Letzteres nennt ausdrücklich **alle KI-Werkzeuge**, die für
Lösungsfindung und Dokumentation genutzt wurden.

### 3.12 Anhang

Jeder Anhangsabschnitt wird im Text mindestens einmal referenziert.

## 4 Abbildungen

- Jede Abbildung hat eine fortlaufende Nummer und eine Bildunterschrift und wird mindestens einmal im
  Text als klickbarer Verweis (`\autoref`) referenziert.
- Schriftgrößen in Abbildungen passen zur Dokumentschrift; bei Screenshots ggf. Teilausschnitte.
- **Blockdiagramme mit Netzwerkkommunikation:** an jedem Pfeil das Protokoll, an den Pfeilspitzen
  (S) = Server bzw. (C) = Client. Software-Blockdiagramme zeigen den Datenfluss.
- **Sequenzdiagramme:** durchgezogen + ausgefüllte Spitze = synchron; durchgezogen + offene Spitze =
  asynchron; gestrichelt = Antwort.
- **Programmablaufpläne (DIN 66001):** Start- und Stop-Terminator, keine offenen Enden, Raute mit
  genau zwei Ausgängen.

## 5 Quellen und Zitierstil (IEEE-orientiert)

### 5.1 Format

```
Online: [Nr] V. Nachname (oder Organisation): „Titel kursiv" weitere Angaben (JJJJ-MM-TT),
        Online: URL als Hyperlink (Zugriff am JJJJ-MM-TT)
Print:  [Nr] V. Nachname (oder Organisation): „Titel kursiv" weitere Angaben, Ort: Verlag, Jahr.
```

Zugriffsdaten kurz vor der Abgabe prüfen und aktualisieren.

### 5.2 Referenzierung

- Jede Quelle wird mindestens einmal als klickbarer Verweis `[Nr]` zitiert.
- Mehrere Quellen: je ein eigenes Klammerpaar (`[3], [4]`).
- Nummerierung nach Reihenfolge der ersten Nennung, nicht alphabetisch — automatisch über BibTeX.

### 5.3 Primärquellen

Standards, Protokolle, Programmiersprachen und Datenformate mit der Primärquelle belegen (RFC,
Spezifikation, offizielle Sprachreferenz).

### 5.4 Detailangaben

Bei Bedarf Kapitel oder Abbildung der Quelle angeben: `\cite[Kap.~9]{rfc9110}`.

## 6 Bewertung (typische Gewichtung)

| Bestandteil | Gewicht |
|-------------|---------|
| Technische Arbeitsergebnisse | ca. 40–45 % |
| PDF-Dokument | ca. 40–45 % |
| Abschlussvortrag | ca. 10–20 % |

Die Dokumentqualität zählt ungefähr so viel wie das technische Ergebnis. Eine sehr gute Gesamtnote
setzt voraus, dass alle drei Teile sehr gut sind.
