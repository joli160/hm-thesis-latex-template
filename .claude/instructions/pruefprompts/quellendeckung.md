# Prüfprompt: Belegdeckung (Aussage ↔ Quelleninhalt)

Prompt D prüft Format und Vollständigkeit. Dieser Prompt prüft die riskantere Frage:

> **Steht die Aussage, die im Text belegt wird, tatsächlich in der zitierten Quelle?**

Ein formal korrektes Zitat, das eine Aussage stützt, die die Quelle nicht trifft, ist ein Fehlzitat —
deutlich schwerer als ein Formatfehler. Sprachmodelle ordnen Quellen gern nach Plausibilität zu; genau
das fängt dieser Prompt ab.

**Einstellungen:** frische Session, Effort `high`, Web-Zugriff Pflicht. Bei vielen Quellen in Etappen
laufen lassen — der Prompt verbietet stilles Überspringen.

```
Prüfe die BELEGDECKUNG meiner Abschlussarbeit: Für jede Zitatstelle muss die zitierte Quelle die dort
behauptete Aussage tatsächlich enthalten. Formatfragen interessieren hier NICHT.

SCHRITT 1 — Inventar: Lies latex/literatur.bib und alle \cite-Stellen in latex/chapters/*.tex (auch \cite[...]{...}).
Arbeitsliste: Datei:Zeile | Key | die konkrete Aussage als überprüfbarer Satz — nicht "es geht um X",
sondern "X unterstützt Y nicht unter Windows". Ein Key an mehreren Stellen ergibt MEHRERE Prüffälle.

SCHRITT 2 — Jede Online-Quelle tatsächlich abrufen. Nicht aus dem Gedächtnis, nicht aus dem Titel,
nicht aus Plausibilität urteilen. Bei Detailangaben die konkrete Unterseite abrufen und Kapitelnummer
und -titel prüfen. Print- oder bezahlte Quellen: "nicht verifizierbar" und sagen, worauf sich die
Annahme stützt. Erfinde NIEMALS einen Seiteninhalt.

SCHRITT 3 — Bewerten mit WÖRTLICHEM Belegzitat aus der Quelle (Originalsprache). Ohne tragenden Satz
ist die Aussage NICHT gedeckt. Kategorien:
  GEDECKT | TEILGEDECKT (Kern stimmt, ein Attribut/Zahlwert nicht — genau benennen) |
  NICHT GEDECKT | FALSCHE QUELLE | NICHT VERIFIZIERBAR

SCHRITT 4 — Gegenrichtung: Aussagen in Grundlagen, Konzipierung und Implementierung, die einen Beleg
BRAUCHEN, aber keinen haben: Zahlen, Versionen, Eigenschaften fremder Technologie ("X ist schneller
als Y"), Verhalten fremder Software, Standards. Aussagen über MEINE Implementierung, Messungen und
Entscheidungen brauchen keinen externen Beleg.

SCHRITT 5 — URLs mit 404/403/Timeout oder Umleitung auf anderen Inhalt melden.

AUSGABE:
(A) Prüffälle nach Schwere sortiert: Stelle | Key | Aussage | Kategorie | Belegzitat | Fix
(B) Unbelegte Behauptungen: Stelle | Behauptung | warum belegpflichtig | Quellenvorschlag nur, wenn
    tatsächlich abgerufen und gelesen — sonst "zu recherchieren"
(C) Bilanz je Kategorie und ausdrücklich: welche Prüffälle NICHT bearbeitet wurden.

REGELN: Read-only. Kein Belegzitat = keine Deckungsbehauptung. Keine erfundenen URLs, RFC- oder
STD-Nummern (nicht jeder RFC hat eine STD-Nummer). Im Zweifel TEILGEDECKT mit Begründung. Ein leerer
Befund ist ein Ergebnis.
```

## Warum der Prompt so gebaut ist

| Element | Zweck |
|---|---|
| Aussage als überprüfbarer Satz | verhindert die Scheinprüfung „Quelle handelt von X, Zitat steht bei X, passt" |
| Ein Key = mehrere Prüffälle | Dokumentationsseiten werden oft für mehrere Aussagen zitiert, nur eine davon ist gedeckt |
| Wörtliches Belegzitat als Pflicht | stärkster Schutz gegen Halluzination: Wer zitieren muss, muss gelesen haben |
| Kategorie TEILGEDECKT | fängt den häufigsten realen Fall: Kern stimmt, ein Adjektiv oder Zahlwert nicht |
| Gegenrichtung | Formalprüfungen finden nur falsche Zitate, nie fehlende |
| Ausnahme für die eigene Arbeit | sonst markiert der Agent die halbe Arbeit als „unbelegt" |
| Meldepflicht für Lücken | macht unvollständige Abdeckung sichtbar statt stillschweigend |

Bewusst getroffene Ausnahmen (z. B. eine Print-Quelle, die immer „nicht verifizierbar" bleibt) als
Kommentar in den Kopf von `latex/literatur.bib` schreiben — dann meldet der nächste Durchgang sie nicht als
neuen Befund.
