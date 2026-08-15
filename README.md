# Spielestatistik

Eine Website, auf der Freundesgruppen ihre Ergebnisse in verschiedenen
Spielen/Disziplinen eintragen und daraus Statistiken erhalten — sowohl in
einzelnen Disziplinen als auch insgesamt. Die Frage, die das Projekt
beantworten soll: Wer ist eigentlich der Beste?

## Stand

Das Projekt ist in Arbeit. V1 soll bis zum 30.09.2026 stehen und umfasst
zunächst nur: Spieler anlegen, Ergebnisse eintragen, Siegquote sehen,
auf dem Handy bedienbar. Eine disziplinübergreifende Gesamtwertung ist
das Ziel, aber noch nicht Teil von V1.

## Technik

HTML/CSS/JavaScript, GitHub, Vercel, Supabase.

## Entscheidungen

**Kein Framework, sondern JavaScript.**
Ein Framework würde in diesem Projekt kaum Aufwand sparen, da kaum
gleichzeitige Zustände vorliegen — der Einarbeitungsaufwand lohnt sich
damit nicht. Außerdem lerne ich ohne Framework erst einmal, wie der
Browser selbst funktioniert.

**Web statt native App.**
Die Einstiegshürde für neue Nutzer ist bei einer Website deutlich
geringer, was wichtig ist, da ohne niedrige Hürde niemand einträgt und
das Projekt nutzlos wird. Außerdem braucht man nur eine Codebasis und
muss nicht iOS und Android bedienen. Dazu kommen sofortige Updates, die
bei einer Website innerhalb weniger Minuten für die Nutzer zugänglich
sind.

**Teilnahmen als eigene Zeilen im Datenmodell, nicht als Spalten.**
Da bei verschiedenen Disziplinen die Anzahl der Spieler variiert, macht
eine einzelne Tabelle keinen Sinn. Man wüsste nicht, wie viele Spalten
man braucht, und müsste in jeder einzelnen Spalte nach dem jeweiligen
Namen suchen. Bei Teamspielen reicht es außerdem nicht zu wissen, wer
mitgespielt hat — man muss wissen, auf welcher Seite. In der
Spalten-Variante bräuchte man dafür eine zusätzliche Spalte pro Spieler.
Stattdessen zwei Tabellen: einmal Spiel (Datum, Disziplin) und einmal
Teilnahmen (Spiel, Spieler, Seite, Ergebnis). So bleibt die Tabelle
immer gleich breit und wird nur länger.

**Für V1 kein Login.**
Normalerweise bräuchte man ein Loginsystem, um sicher zu wissen, dass
die eingeloggte Person auch am Spiel beteiligt war und berechtigt ist,
Eingaben zu ändern. Für V1 lohnt sich der Aufwand nicht, da das Ziel
zunächst nur Ergebnisse eintragen und Siegquote sehen ist; das kommt zu
einem späteren Zeitpunkt. Außerdem erhöht ein Login wieder die
Einstiegshürde zum Eintragen. Damit niemand schummelt, werden
Änderungen an den Einträgen transparent angezeigt, sodass jeder sehen
kann, was geändert wurde.

## Später

In dieser Reihenfolge geplant:

1. Zweite und dritte Disziplin
2. Teams und Gruppen
3. Accounts und vollständiges Änderungsrechte-Modell: nur Beteiligte
   dürfen ändern, die anderen werden benachrichtigt
4. Gesamtwertung über Disziplinen hinweg (Elo pro Disziplin), da eine
   reine Siegquote den bevorzugt, der nur gegen Schwächere spielt
5. Statistiken mit Erzählwert: beste Teampartner, Rivalitäten,
   Siegesserien

Zusätzlich vorgemerkt:

- Platzierungen statt nur Sieg/Niederlage bei Disziplinen mit Rangfolge
- Poker: Wertung über Geldbetrag pro Spieler statt über einen Gewinner
- Zeitraum-Filter für Statistiken (gesamt / letzte 20 Spiele / letzter Monat)
- Team-Statistiken, nicht nur pro Einzelspieler
