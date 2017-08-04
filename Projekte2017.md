# Projekte der Veranstaltung "Fortgeschrittene funktionale Programmierung in Haskell"

## Bestehenskriterien

Zum Bestehen der Veranstaltung müssen Sie insgesamt (Übung + Projekt) 220 Punkte erreichen.

Die Punkte sind unterteilt in Kategorien, aus denen nicht mehr als die angegebene Anzahl berücksichtigt wird:

- Parser: 50 Punkte
- div. Libraries: 60 Punkte
- "Core"-Haskell: 80 Punkte ("Core"-Haskell umfasst die Libraries `lens`,`mtl` bzw. `transformers`,`attoparsec` oder andere Parser,`gloss` oder andere GUI)
- Visualisierung: 80 Punkte
- Parallelism/Concurrency: 50 Punkte
- Binärparsing: 25 Punkte

Dies dient dazu, dass man sich nicht nur auf eine Sache konzentriert, sondern verschiedene Aspekte und deren Zusammenspiel verstanden haben muss.

Die im Folgenden beschriebenen Projekte sind alle offen gehalten. Wenn ihnen eine sinnvolle Erweiterung einfällt, sprechen sie die Tutoren an und diese Erweiterung wird in dieses Dokument aufgenommen und eine Bepunktung hierfür festgelegt.

Für alle Projekte gilt: **Bitte schreiben Sie ordentlichen Code. Organisieren Sie Ihren Code in sinnvollen Modulen. Geben Sie Typsignaturen mit an. Im Zweifelsfall dokumentieren Sie ihren Code. Liefern Sie außerdem eine Projektbeschreibung mit Bedienungsanleitung mit.**

## Projekte

Von den Projekten "Sokoban" und "Snake" darf nur eines gewählt werden.

### Sokoban (Punkte: 80 + 80 (optional))

Spielbeschreibung: [Sokoban](https://en.wikipedia.org/wiki/Sokoban) ist ein kachel- und rundenbasiertes Puzzlespiel (ähnlich wie `Game` aus den Übungen), in dem es darum geht, alle Kisten auf markierte Zielpunkte zu schieben (mit nur wenig Platz für Manöver). [Hier](https://en.wikipedia.org/wiki/Sokoban#/media/File:Sokoban_ani.gif) finden Sie ein Beispiellevel, das alle Basisregeln deutlich macht. 

#### Bepunktung

Mindestanforderungen:
Das Spiel muss fehlerfrei spielbar sein (also: Siegbedingungen überprüfen, korrekte Kollisionsabfrage, . . . ), bei erfolgreich absolviertem Level automatisch das nächste Laden und einen Counter enthalten, wie viele Züge in diesem Level bereits getätigt wurden. Die Spiellogik soll über einen State (auch als RWST möglich) abgehandelt werden. Es sollen verschiedene spielbare Level vorliegen, die bei Spielstart aus einer oder mehreren externen Textdateien geladen werden sollen (Definieren Sie eine Repräsentation für Level und schreiben Sie den entsprechenden Parser). Eine grafische Oberfläche ist Pflicht (Ausgabe auf der Konsole genügt nicht!), die Wahl der GUI-Bibliothek (gloss, not-gloss, sdl2, gtk2hs,...) steht Ihnen jedoch frei. 

- Visualisierung: 15 Punkte (Visualisierung)
- Level-Parser: 20 Punkte (Parser)
- Benutzung von State oder RWST: 25 Punkte (Core)
- Implementation Spiellogik: 20 Punkte (Core)

Optionale Zusätze:
Zusätzliche Feature müssen auch in den mitgelieferten Levels auftauchen. 

- Verwendung von Lens: 10 Punkte (Core)
- Einlesen/Anzeigen von Bildern mittels Library: 5 Punkte (div. Libraries)
- Binärparser für Bitmaps und Anzeigen: 25 Punkte (Binärparsing)
- Gameplay-Features: 
  - Türen (die man mit Schlüssel öffnen kann): 4 Punkte (Core) + 2 Punkte (Visual.)
  - Handschuhe (die eingesammelt Ziehen von Kisten ermöglichen): 4 Punkte (Core) + 2 Punkte (Visual.)
  - Undo/Redo: 10 Punkte (Core)
  - Speicherfunktion: 10 Punkte (Core)
  - Replayfunktion: 8 Punkte (Core) +  2 Punkte (Visual.)
  - ...

### Snake (Punkte: 50 + 50 (optional))

[Snake](https://en.wikipedia.org/wiki/Snake) mit verschiedenen Level programmieren. Snake ist gut für eine Multiplayer-Implementation geeignet. 

Spielbeschreibung: Wenn kein Essen auf dem Spielfeld zu sehen ist, dann erscheint auf einem freien Feld etwas zu Essen. Die Schlange kann gesteuert werden, läuft aber automatisch nach vorn, wenn keine Taste gedrückt wurde. Wenn der Kopf der Schlange Essen aufnimmt, dann verschwindet es und die Schlange beginnt zu wachsen. Ziel des Spiel ist es möglichst viele Punkte (Essen) zu sammeln, bevor die Schlange vor die Wand oder sich selbst läuft.

Level-Variante: Wenn ein Level an der Außenseite keine Wand hat, dann kommt die Schlange auf der anderen Seite des Levels wieder herein.

#### Bepunktung

Mindestanforderung: 
Das Spiel ist gemäß der obigen Beschreibung fehlerfrei spielbar. Es gibt verschiedene Level (mit und ohne Wände), die beim Spielstart aus einer oder mehreren Textdateien geparst werden. Eine grafische Oberfläche ist Pflicht (Ausgabe auf der Konsole genügt nicht!), die Wahl der GUI-Bibliothek (gloss, not-gloss, sdl2, gtk2hs,...) steht Ihnen jedoch frei. 

- Visualisierung: 15 Punkte (Visualisierung)
- Level-Parser: 15 Punkte (Parser)
- Implementation Spiellogik: 20 Punkte (Core)

Optionale Zusätze:
Zusätzliche Feature müssen in der Projektbeschreibung und auch in den mitgelieferten Levels auftauchen. 

- Benutzung von State oder RWST: 25 Punkte (Core)
- Verwendung von Lens: 10 Punkte (Core)
- Einlesen/Anzeigen von Bildern mittels Library: 5 Punkte (div. Libraries)
- Binärparser für Bitmaps und anzeigen: 25 Punkte (Binärparsing)
- Highscore-Screen (angezeigt beim Pausieren/nach Spielende): 8 (Core) + 4 (Visualisierung)
- Items (beschleunigt, verbreitert o.ä. temporär... ): 4 (Core) + 2 (Visualisierung)

Multiplayer: Jeder Spieler steuert eine Schlange. Tote Schlangen verschwinden vom Spielfeld. Wer zuletzt überlebt, hat gewonnen.

- Multiplayer an einem PC: 10 Punkte (Core)
- Multiplayer über Netzwerk: 10 Punkte (Concurrency) + 10 Punkte (Binärparsing) + 15 Punkte (Core)
- Dedizierter Multiplayer-Server: 25 Punkte (Concurrency)

### Datamining (Punktesumme: 35 + 45 (optional))

Es wird ihnen eine CSV-Datei des Haushaltsplanes der Landesregierung NRW von 2015 gegeben. Lesen die Datei ein und visualisieren sie diese in einer geeigneten Weise. Für eine optionale interagierbare Visualisierung gibt es die 20 optionalen Visualisierungspunkte.

#### Bepunktung

- Parsing von CSV-Daten mit `,` und `\n`: 7 Punkte (Parser)
- Verifikation der Daten: 3 Punkte (Parser)
- Erstellung der Visualisierung: 25 Punkte (Visualisierung)

Optionale Zusätze:

- Erkennen/Angeben von Feldtrennern und Zeilentrennern: 7 Punkte (Parser)
- Sinnvolle interaktive Visualisierung: 10 (Core) + 20 Punkte (Visualisierung) - z.b. wie [Wuppertraler Haushaltsdaten](http://offenerhaushalt.opendatal.de/#produkte/year=2012&art=Ergebnis)
- Daten im JSON-Format annehmen: 8 Punkte (Parser) bei selbst-schreiben, 8 Punkte (div. Libraries) bei Nutzung von externen Libs.

### Verteiltes Rechnen (Punktesumme: 25 + 78 (optional))

Dieses Projekt entspricht dem Betriebssysteme-Projekt des rechnenden Servers. Ihr Programm soll einen Port öffnen und dort Verbindungen akzeptieren. Diese schicken "Aufträge" (simple Arithmetik mit `+-*/`) an den Server, der einige Zeit brauchen soll, diese zu bearbeiten (2-30 Sekunden). Man kann mehrere "Jobs" starten, sich nach ihrem Zustand erkundigen, die Ergebnisse abholen oder auf Ergebnisse warten.

#### Bepunktung

- Minimal-Server: 25 Punkte (Parallelism/Concurrency)

Optionale Zusätze:

- Parsing der Eingaben mittels Parser: 5 Punkte (Parser)
- Verwendung von Lenses: 8 Punkte (Core)
- Verteiltes Rechnen: 25 Punkte (Parallelism/Concurrency) + 45 Punkte (div. Libraries) bei Verwendung von CloudHaskell - man rechnet nicht auf einem Server, sondern auf einer Cloud

### Jabber-Bot (Punktesumme: 33 + 72 (optional))

Das XMPP-Protokoll (auch Jabber genannt) int eine offene Schnittstelle. Über die Techfak bekommen sie einen eigenen Jabber-Account (username@techfak.de). Schreiben sie einen Bot, der einfache Aufgaben in einem Jabber-Chat (oder Konferenz) übernimmt.

#### Aufgaben:

- Remember-me: Der Bot reagiert auf ein Kommando der Form "remind me at 13:45: go eat in Mensa" und um 13:45 schreibt der Bot den Absender mit der Nachricht "go eat in Mensa" an.
- Wikipedia-suche: Der Bot reagiert auf ein Kommando der Form "wiki universität bielefeld" und sucht auf Wikipedia nach "universität bielefeld", nimmt den ersten Treffer und antwortet mit dem ersten Absatz des Artikels
- Kalender-Plugin: Das ekVV stellt den persönlichen Kalender im caldav-Format zur Verfügung. Laden sie diesen zum Start/auf Wunsch ein und senden sie vor jedem Event eine Nachricht an den jeweiligen User.
- Verteiltes-Rechnen-Plugin: Wenn sie das Projekt "verteiltes Rechnen" gemacht haben, dann sollen sie auch in der Lage sein über ihren Bot mit dem jeweiligen Server zu reden (und so Aufträge absenden, abholen etc.).
- Webprojekt-Plugin: Wenn das Webprojekt ebenfalls gemacht wurde, dann soll dieser Bot in der Lage sein private Nachrichten an den jeweiligen User weiterzuleiten.

#### Bepunktung

- Aufsetzen des Bots: 25 Punkte (div. Libraries)
- Remember-Me-Aufgabe: 8 Punkte (Core)

Optionale Zusätze:

- Wikipedia-Suche-Aufgabe: 16 Punkte (Core) + 8 Punkte (div. Libraries) bei Verwendung von hexpat-lens zum Antwort-Parsen
- Kalender-Plugin:
    - Parser für ekvv-Kalender: 16 Punkte (Parser) oder 16 Punkte (div. Libraries)
    - Implementation Erinnerungsfunktion: 8 Punkte (Core)
- Verteiltes Rechnen-Plugin:
    - Bot baut eine Verbindung zum Projekt "Verteiltes Rechnen" auf und leitet Inzut/Output durch: 8 Punkte (Parser) + 8 Punkte (Core)
- "Webprojekt"-Plugin:
    - Notifications vom Forum per Jabber verstehen und an den angegeben User weiterleiten: 8 Punkte (Core)


### Webprojekt (Punktesumme: 50 + 66 (optional))

Erstellen sie ein simples Forum. Die Registrierung kann entweder über Email/Passwort oder auch per Plugins, wie "OAuth" (ekvv, Google, Facebook, Github, Twitter, Twitch, ...) ermöglicht werden.

Das Admin-Panel soll umfassen:
- Hinzufügen/Entfernen von Foren
- Moderations-Fähigkeiten
- Rechteverwaltung (Benennen von "Moderatoren", einschränken der Rechte auf Unterforen)

#### Bepunktung

- Minimal-Forum: 40 Punkte (div. Libraries) + 7 Punkte (Core)
- Registrierung: 3 Punkte (div. Libraries)

Optionale Zusätze:

- Gute responsive Visualisierung mittels Bootstrap (o.ä.): 30 Punkte (Visualisierung)
- Upload von Avataren und deren Darstellung: 5 Punkte (div. Libraries)
- Admin-Panel: 15 Punkte (Core)
- Notifications per E-Mail: 8 Punkte (Core)
- Notifications per Jabber: 8 Punkte (div. Libraries)


# Abgabedatum: ?????.2017

Projekte werden vorzugsweise als Projekt auf Github oder über euer __[Remote-Folder](https://techfak.net/dienste/remote/files#git)__  abgegeben. Wir helfen in den Tutorien auch bei der Benutzung von git bzw. bei der Rechtevergabe im Remote-Verzeichnis. Bitte vermeidet es temporäre Dateien (insb. das `.stack-work`-Verzeichnis) in euer git hinzuzufügen. Legt eine [`.gitignore`](https://git-scm.com/docs/gitignore) an, damit sowas nicht zufällig passiert. 

