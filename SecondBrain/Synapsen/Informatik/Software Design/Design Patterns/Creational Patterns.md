Creational Design Patterns befassen sich mit Mechanismen zur effizienten Erstellung von Objekten. Sie erhöhen die Flexibilität und Wiederverwendbarkeit von existierendem Code.

## Singleton
Das Singleton ist eines der beliebtesten und meistgenutztesten Design Patterns in Programmen heutzutage.

```Java
class MySingleton() {
	private static MySingleton instance;

	public static MySingleton getInstance() {
		if (instance == null) {
			instance = new MySingleton();
		}

		return instance;
	}
}
```

*Merkmale:*
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

```Java
abstract class Shape implements Cloneable {
	void clone();
	String whoami();
}

class Triangle() extends Shape {
	void clone() {
		return new Triangle();
	}

	String whoami() {
		return "I am a Triangle";
	}
}

class Circle() extends Shape {
	void clone() {
		return new Circle();
	}

	String whoami() {
		return "I am a Circle with";
	}
}

public class Demo {
	private Circle originalCircle = new Circle();
	
    public static void main(String[] args) {
	    Shape shape1 = getShape();
	    shape1.whoami();
    }
    
	statid Shape getShape() {
		System.out.println("Returning cloned entity of Circle");
		return originalCircle.clone();
	}  
}
```

*Merkmale:*
- Existierende Objekte werden geklont
- Klonprozess wird delegiert (über Interface)
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
interface Game {
	
}

class Chess implements Game {
	
}

class Scribble implements Game {
	
}

class GameCreator {
	abstract BoardGame createGame();
}

class ChessGameCreator extends GameCreator {
	Chess createGame() {
		return new Chess();
	}
}

class ScribbleGameCreator extends GameCreator {
	Scribble createGame() {
		return new Scribble();
	}
}

public class Demo {
    private static GameCreator gameCreator;
    private static Game game;

    public static void main(String[] args) {
        configure();  
        runBusinessLogic();
    }

	// Factory method
    static void configure() {
        if (System.getProperty("game").equals("Chess")) {
            gameCreator = new ChessGameCreator();
        } else {
            gameCreator = new ScribbleGameCreator();
        }
    }

	// Using of resulting instance of GameCreator
	static void runBusinessLogic {
		game = gameCreator.createGame();
	}
}
```

*Merkmale:*
- Logik zum Erstellen der Objekte wird versteckt
- Aufruf einer speziellen Factory-Methode

## Abstract Factory
auch genannt: *Kit*

Dieses Design Pattern wird benutzt, wenn wir verschiedene Objekte haben, die logisch zueinander gehören und nicht vermischt werden dürfen.

```Java
interface Board {

}

class ChessBoard implements Board {

}

class ScribbleBoard implements Board {

}

interface Pieces {

}

class ChessPieces implements Pieces {

}

class ScribblePieces implements Pieces {

}

class GameFactory {
	abstract Board createBoard();
	abstract Pieces createPieces();
}

class ChessGameFactory extends GameFactory {
	ChessBoard createBoard() {
		return ...;
	}
	
	ChessPieces createPieces() {
		return ...;
	}
}

class ScribbleGameFactory extends GameFactory {
	ScribbleBoard createBoard() {
		return ...;
	}
	
	ScribbleBoard createPieces() {
		return ...;
	}
}

public class Demo {
    public static void main(String[] args) {
	    GameFactory gameFactory = getFactory();
	    gameFactory.createBoard()
	    gameFactory.createPieces()
    }

	static GameFactory getFactory() {
		if (...) {
			return new ChessFactory();
		} else {
			return new ScribbleFactory();
		}
	}
}
```

## Builder + Director
Beim Builder und Director Pattern übergibt man dem Director den Builder. Der Director ruft dann nacheinander die benötigten Funktionen vom Builder auf und speichert sich eine Referenz auf das Objekt.

Man nutzt dieses Pattern vor allem dann, wenn es nicht möglich ist eine Basisklasse zwischen den Objekten einzuführen - Um die Funktionalitäten nicht doppelt bzw. für jedes Objekt schreiben zu müssen. Man packt sie stattdessen in den Builder und das "wie" steckt im Director.

![[builder-and-director-pattern.png]]

*Merkmale:*
- Das Objekt lebt im ConcreteBuilder.
- Die Erzeugung wurde vom Objekt selbst getrennt.