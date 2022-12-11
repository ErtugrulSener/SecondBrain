Creational Design Patterns befassen sich mit Mechanismen zur effizienten Erstellung von Objekten. Sie erhöhen die Flexibilität und Wiederverwendbarkeit von existierendem Code.

## Singleton
Das Singleton ist eines der beliebtesten und meistgenutztesten Design Patterns in Programmen heutzutage.

Merkmale:
- Single Instance
	- Es gibt nur eine Instanz des Objektes
- Global Access
	- Das Objekt kann vom gesamten Programm referenziert werden (über statische public Methoden)
- Lazy Loading
	- Objekte werden erst instanziiert, wenn sie gebraucht werden

## Prototype
Weitere Namen für das Design Pattern sind:
- Virtual Copy Constructor
- Clone

Das Prototype Pattern wird vor allem für Klonvorgänge genutzt, bei der der Client die geklonte Klasse womöglich nicht kennt, sondern nur ein Interface (das die Zielklasse implementiert).

Merkmale:
- Existierende Objekte werden geklont
- Klonprozess wird delegiert (über Interface)
- Common Interface
- Genau eine "clone" Methode
- Private Felder können im Klonprozess mitkopiert werden

## Factory Method
Weitere Namen für das Design Pattern sind:
- Virtual Constructor

Eine 'Factory Method' ist eine Methode, die ein Objekt generiert.
Man benötigt dieses Pattern immer, wenn man mehr braucht, als einen simplen Konstruktor.

```Java
class ChessGameCreator {
	Chess chessCreator() {
		Chess chess = new Chess();
		chess.setState(0);
		return chess;
	}
}
```

Sehr nützlich wird das Factory Method Pattern aber erst, wenn Polymorphismus genutzt wird. Es gibt es ein Basisinterface, das eine Methode deklariert. Alle Klassen, die das Interface implementieren, überschreiben dabei diese Methode mit ihrer Implementierung.

Man denke an folgendes Szenario:

```Java
interface BoardGame {
	
}

class Chess implements BoardGame {
	
}

class Scribble implements BoardGame {
	
}

class Game {
	abstract BoardGame createGame();
}

class ChessGameCreator extends Game {
	Chess createGame() {
		return new Chess();
	}
}

class ScribbleGameCreator extends Game {
	Scribble createGame() {
		return new Scribble();
	}
}

main() {
	Game chessGame = new ChessGameCreator();
	chessGame.createGame();
}
```

Merkmale:
- Logik zum Erstellen der Objekte wird versteckt
- Aufruf einer speziellen Factory-Methode

## Abstract Factory
#@ Wie lässt sich dieses Design Pattern beschreiben?

#@ Wie nennt man es auch noch?

## Builder + Director
#@ Wie kann man dieses Pattern beschreiben?