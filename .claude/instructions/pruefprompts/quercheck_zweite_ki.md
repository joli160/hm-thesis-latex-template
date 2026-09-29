# Quercheck mit einer zweiten KI

Ein Modell, das einen Text geschrieben oder überarbeitet hat, übersieht seine eigenen Muster. Ein
anderes Modell (anderer Anbieter oder zumindest eine frische Session ohne Vorgeschichte) liest ihn wie
ein fremder Gutachter und findet eher, was in der Schreibsession durchgerutscht ist: KI-typische
Formulierungen, Widersprüche, Stellen, die nur mit dem Vorwissen der Session verständlich sind.

**Reihenfolge:** erst selbst lesen, dann Quercheck. Der Quercheck ersetzt das eigene Lesen nicht —
er findet andere Dinge.

## Vorgehen

1. Ein Kapitel (oder einen Abschnitt) als Text kopieren — LaTeX-Quelltext ist in Ordnung.
2. Prompt unten davor setzen, Vorgaben und Checkliste aus `vorgaben.md` / `schreibkonventionen.md`
   mitgeben, wenn das Werkzeug keinen Dateizugriff hat.
3. Befunde **nicht blind übernehmen**. Jeder Punkt ist ein Hinweis, den du selbst entscheidest.
   Vorschläge der zweiten KI sind genauso ungeprüft wie die der ersten.
4. Keine vertraulichen Inhalte in ein Werkzeug geben, das dafür nicht freigegeben ist.

## Prompt

```
Du bist Gutachter einer Abschlussarbeit an einer technischen Hochschule. Lies den folgenden
Kapitelausschnitt kritisch. Ändere nichts am Text; liefere nur Befunde.

Prüfe:
1. Stellen, die nach KI-generiertem Text klingen: Floskeln, leere Dreiklänge, "nicht nur … sondern
   auch", zusammenfassende Schlusssätze, unbelegte Steigerungen, gleichförmige Absätze, Aufzählungen
   statt Argumentation. Zitiere jeweils die Stelle.
2. Aussagen, die ein Gutachter hinterfragen würde: unbelegte Behauptungen, Zahlen ohne Herkunft,
   Bewertungen ohne Kriterium.
3. Logische Lücken und Widersprüche innerhalb des Ausschnitts.
4. Stellen, die ohne Vorwissen unverständlich sind.

Ausgabe als Tabelle: Zitat | Befund | Schwere (hoch/mittel/niedrig) | Vorschlag.
Maximal 20 Befunde, die schwersten zuerst. Wenn der Text in einem Punkt in Ordnung ist, sag das —
konstruiere keine Probleme.

--- AUSSCHNITT ---
<Text hier einfügen>
```
