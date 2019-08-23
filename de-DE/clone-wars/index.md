---
title: Klonkriege
description: Erstelle ein Spiel in dem du den Planet Erde vor den Weltraummonstern retten musst.
layout: project
notes: "Clone Wars - notes.md"
---

# Introduction { .intro }

In diesem Projekt lernst du, wie man ein Spiel erstellt, in dem du den Planet Erde vor Weltraummonstern retten musst.

<div class="scratch-preview">
  <iframe allowtransparency="true" width="485" height="402" src="https://scratch.mit.edu/projects/embed/46018140/?autostart=false" frameborder="0"></iframe>
  <img src="images/invaders-final.png">
</div>

# Schritt 1: Ein Raumschiff bauen { .activity }

Lass uns als erstes ein Raumschiff bauen, das die Erde verteidigen wird!

## Aktivitäts-Checkliste { .check }

+ Starte ein neues Scratch Projekt und lösche das Katzen- Sprite, damit dein Projekt leer ist. Du findest den online Scratch Editor unter <a href="http://jumpto.cc/scratch-new" target="_blank">jumpto.cc/scratch-new</a>.

+ Füge den 'stars' (Sterne) HIntergrund und das 'Spaceship' (Raumschiff) Sprite zu deinem Projekt hinzu. Schrumpfe dein Raumschiff und bewege es zum unteren Teil deines Bildschirms.

	![screenshot](images/invaders-sprites.png)

+ Füge den Code hinzu, um dein Raumschiff nach links zu bewegen, wenn die linke Pfeiltaste betätigt wird. Du musst diese Blöcke hierfür benutzen:

	```blocks
		Wenn die grüne Flagge angeklickt
		wiederhole fortlaufend
  			 falls <Taste [Pfeil nach links v] gedrückt?> dann
     			 ändere x um (-4)
   			Ende
		Ende
	```

+ Füge den Code hinzu, um dein Raumschiff nach rechts zu bewegen wenn die rechte Pfeiltaste gedrückt wird.

+ Teste dein Projekt, um zu sehen, ob du dein Raumschiff mit den Pfeiltasten steuern kannst.

## Projekt speichern { .save }

# Schritt 2: Blitze { .activity }

Lass uns dem Raumschiff die Fähigkeit verleihen, Blitze abzufeuern!

## Aktivitäts-Checkliste { .check }

+ Füge das 'Lightning' (Blitze) Sprite von der Scratch Bibliothek hinzu.  Wenn das Spiel beginnt, sollten die Blitze erstmal versteckt bleiben bis das Raumschiff seine Laser-Kanonen feuert. Das Sprite muss viel kleiner und kopfüber sein. Füge den folgenden Code zum 'Lightning' (Blitze) Sprite hinzu.

	```blocks
		Wenn die grüne Flagge angeklickt
		verstecke dich
		setze Größe auf (25)%
		setze Richtung auf (-90 v)	
	```


+ Füge den folgenden Code **to the Spaceship** (zum Raumschiff hinzu), um einen neuen Blitz zu erzeugen, wannimmer die Leertaste gedrückt wird.


	```blocks
		Wenn die grüne Flagge angeklickt
		wiederhole fortlaufend
   			falls <Taste [Leertaste v] gedrückt?> dann
      			erzeuge Klon von [Lightning v]
   		Ende
	Ende
	```

+ Wannimmer ein neuer Klon erstellt wird, sollte er am gleichen Ort wie das Raumschiff beginnen und dann das Stadium hoch gehen bis er die Kante berührt. Füge den folgenden Code **to the Lightning sprite** (zum Blitze-Sprite hinzu):

	```blocks
		Wenn ich als Klon entstehe
		gehe zu [Spaceship v]
		zeige dich
		wiederhole bis <wird [Rand v] berührt?>
   			ändere y um (10)
		Ende
		lösche diesen Klon
	```

Hinweis: Wir bewegen den neuen Klon zum Raumschiff hin, während es immer noch versteckt ist, ehe wir es dann zeigen. Das sieht schöner aus.

+ Teste deine Blitze, indem du die Leertaste drückst.

## Projekt speichern { .save }

## Aufgabe: Die Blitze ausbessern {.challenge}
Was passiert, wenn du die Leertaste gedrückt hältst? Kannst du einen `wait` {.blockcontrol} Block einschieben, um dies zu beheben?

## Projekt speichern { .save }

# Schritt 3: Fliegende Weltraum-Nilpfherde { .activity }

Lass uns jetzt ganz viele, fliegende Weltraum-Nilpferde, die versuchen, dein Raumschiff zu zerstören, hinzufügen.

## Aktivitäts-Checkliste { .check }

+ Erstelle ein neues Sprite vom 'Hippo1' (Nilpferd 1) Bild in der Scratch Bibliothek.

	![screenshot](images/invaders-hippo.png)

+ Stelle dessen Rotationsstil so ein, dass es sich nur links-rechts drehen kann und füge den folgenden Code hinzu, um das Sprite zu verstecken, wenn das Spiel beginnt:

	```blocks
		Wenn die grüne Flagge angeklickt
		verstecke dich
	```

+ Erstelle eine neue Variable namens `speed` {.blockdata} (Geschwindigkeit), die nur für das Nilpferd- Sprite gedacht ist.

	![screenshot](images/invaders-var.png)

	Du wirst wissen, ob du es richtig gemacht hast, weil der Name für die Variable des Sprites daneben stehen wird:

	![screenshot](images/invaders-var-test.png)

+ Der folgende Code erzeugt alle paar Sekunden ein neues Nilpferd. **The Stage** (Das Stadium) ist ein guter Platz zur Aufbewahrung dieses Codes:

	```blocks
		Wenn die grüne Flagge angeklickt
		wiederhole fortlaufend
  			warte (Zufallszahl von (2) bis (4)) Sek.
   			erzeuge Klon von [Hippo1 v]
		Ende
	```

+ Wenn jeder Nilpferd-Klon beginnt, lasse ihn sich (bei zufällig ausgewählter Geschwindigkeit) rund herum um das Stadium bewegen bis das Nilpferd vom Blitz getroffen wird. Füge diesen Code **to the hippo**  (zum Nilpferd) Sprite hinzu:

	```blocks
		Wenn ich als Klon entstehe
		setze [speed v] auf (Zufallszahl von (2) bis (4))
		gehe zu x:(Zufallszahl von (-220) bis (220)) y:(150)
		zeige dich
		wiederhole bis <wird [lightning v] berührt?>
   			gehe (speed) er-Schritt
   			drehe dich nach rechts um (Zufallszahl von (-10) bis (10)) Grad
  			 pralle vom Rand ab
		Ende
		lösche diesen Klon
	```

+ Teste deinen Nilpferd-Code. Du solltest alle paar Sekunden einen neuen Nilpferd-Klon sehen können, jeder davon bewegt sich zu seiner eigenen Geschwindigkeit.

	![screenshot](images/invaders-hippo-test.png)

+ Teste deine Laser-Kanone. Wenn du ein Nilpferd triffst, verschwindet es dann?

+ Wenn ein Nilpferd dein Raumschiff berührt, müssen wir dein Raumschiff dazu bringen, dass es explodiert! Um dies zu erreichen, müssen wir als erstes gewährleisten, dass dein Raumschiff 2 Kostüme namens 'normal' (normal) und 'hit' (wurde getroffen) hat.

	![screenshot](images/invaders-spaceship-costumes.png)

	Das 'hit' (wurde getroffen) Kostüm des Raumschiffs kann erstellt werden durch den Import des 'Sun' (Sonne) Bildes aus der Scratch Bibliothek und anschließend das 'Color a shape' (eine Form bemalen) Tool benutzen, um dessen Farbe zu ändern.

	![screenshot](images/invaders-sun.png)

+ Füge diesen Code zu deinem Raumschiff hinzu, damit  es jedes Mal, wenn es mit einem fliegenden Nilpferd zusammenstößt, sein Kostüm ändert:

	```blocks
		Wenn die grüne Flagge angeklickt
		wiederhole fortlaufend
   			wechsle zu Kostüm [normal v]
   			warte bis <wird [Hippo1 v] berührt?>
   			wechsle zu Kostüm [hit v]
   			sende [hit v] an alle
   			warte (1) Sek.
		Ende
	```

+ Hast du bemerkt, dass du in dem o.g. Code eine 'hit' (wurde getroffen) Meldung gesendet hast? Du kannst diese Meldung benutzen, um alle Nilpferde verschwinden zu lassen, wenn das Raumschiff getroffen wurde.

	Füge diesen Code zu deinem Nilpferd hinzu:

	```blocks
		Wenn ich [hit v] empfange
		lösche diesen Klon
	```

+ Teste diesen Code, indem du ein neues Spiel beginnst und mit einem Nilpferd kollidierst. 

	![screenshot](images/invaders-hippo-collide.png)

## Projekt speichern { .save }

## Aufgabe: Leben und Punktzahl {.challenge}
Kannst du `lives` {.blockdata} (Leben), `score` {.blockdata} (Punktzahl) oder sogar eine `highscore` {.blockdata} (hohe Punktzahl) zu deinem Spiel hinzufügen? Du kannst das 'Catch the Dots' (Fang die Punkte) Projekt als Hilfestellung hierfür benutzen.

## Projekt speichern { .save }

# Schritt 4: Flughunde! { .activity }

Lass uns einen Flughund kreieren, der Orangen auf dein Raumschiff wirft.

## Aktivitäts-Checkliste { .check }

+ Lass uns als erstes ein neues Fledermaus-Sprite herstellen, das sich  `forever` {.blockcontrol} (für immer) über dem oberen Teil des Stadiums `move` {.blockmotion} (bewegt).  Denke daran, deinen Code zu testen!

	![screenshot](images/invaders-bat.png)

+ Wenn du dir die Kostüme der Fledermaus ansiehst, wirst du sehen, dass sie bereits 2 hat:

	![screenshot](images/invaders-bat-costume.png)

	Benutze den `next costume` {.blocklooks} (nächstes Kostüm) Block, damit die Fledermaus mit den Flügeln schlägt, während sie sich bewegt.

+ Erstelle in der Scratch Bibliothek ein neues 'Orange' Sprite.

	![screenshot](images/invaders-orange.png)


+ Füge den Code für deine Fledermaus hinzu, damit sie alle paar Sekunden einen neuen, orange-farbenen Klon herstellt.

	```blocks
		Wenn die grüne Flagge angeklickt
		wiederhole fortlaufend
  			warte (Zufallszahl von (5) bis (10)) Sek.
   			erzeuge Klon von [Orange v]
		Ende
	```

+ Klicke auf dein orange-farbenes Sprite und füge diesen Code hinzu, damit jeder orange-farbene Klon das Stadium von der Fledermaus zum Raumschiff hin hinunterfällt:

	```blocks
		Wenn die grüne Flagge angeklickt
		verstecke dich

		Wenn ich als Klon entstehe
		gehe zu [Bat1 v]
		zeige dich
		wiederhole bis <wird [Rand v] berührt?>
  			ändere y um (-4)
		Ende
		lösche diesen Klon

		Wenn ich [hit v] empfange
		lösche diesen Klon
	```

+ In deinem Raumschiff-Sprite musst du deinen Code modifizieren, damit du getroffen wirst, wenn du ein Nilpferd oder eine Orange berührst:

	```blocks
		warte bis <<wird [Hippo1 v] berührt?> oder <wird [Orange v] berührt?>>
	``` 

+ Teste dein  Spiel. Was passiert, wenn du von einer herabfallenden Orange getroffen wirst?

## Projekt speichern { .save }

# Schritt 5: Game Over { .activity }

Lass uns eine 'game over' (Spiel-Ende) Meldung zum Ende des Spiel hinzufügen.

## Aktivitäts-Checkliste { .check }

+ Falls du es noch nicht getan hast, musst du jetzt eine neue Variable namens `lives` {.blockdata} (Leben) erstellen. Dein Raumschiff sollte mit 3 Leben starten und immer ein Leben verlieren, sobald es mit einem Feind zusammenstlößt. Dein Spiel sollte ebenfalls beendet werden, sobald du alle deine Leben verloren hast. Wenn du hierbei Hilfestellung benötigst, kannst nochmal in das 'Catch the Dots' (Fang die Punkte) Projekt schauen.

+ Zeichne ein neues Sprite namens 'Game Over' mit Hilfe des Text Tools.

	![screenshot](images/invaders-game-over.png)

+ Sende eine `game over` {.blockevents} Meldung in deinem Stadium kurz bevor das Spiel aus ist.

	```blocks
		sende [game over v] an alle und warte
	```

+ Füge diesen Code zu deinem 'Game Over' Sprite hinzu, damit die Meldung bei Spiel-Ende angezeigt wird:

	```blocks
		Wenn die grüne Flagge angeklickt
		verstecke dich

		Wenn ich [game over v] empfange
		zeige dich
	```

	Weil du einen Block mit `broadcast [ Game over] and wait` {.blockevents} (Game Over und Warten Meldung) in deinem Stadium benutzt hast, wird es darauf warten, dass das 'Game Over' Sprite angezeigt wird, ehe das Spiel beendet wird.

+ Teste dein  Spiel. Wie viele Punkte kannst zu erzielen? Kannst du an Wege denken, dein Spiel zu verbessern, falls es zu einfach oder zu schwer sein sollte?

## Projekt speichern { .save }

## Aufgabe: Verbessere dein  Spiel {.challenge}
Welche Verbesserungen kannst du bei deinem Spiel vornehmen? Hier sind ein paar Ideen:

+ Füge ein paar Booster-Packs hinzu, die du sammeln kannst, um weitere Leben zu erhalten;

![screenshot](images/invaders-aid.png)

+ Füge frei-schwebende Meteoriten hinzu, denen dein Raumschiff ausweichen muss;
	
![screenshot](images/invaders-rocks.png)

+ Lass noch mehr Feinde erscheinen, wenn deine Punktzahl auf 100 ansteigt.

```blocks
	warte bis <(score) = [100]>
```

## Projekt speichern { .save }
