![[Die 3 Basistypen#Creational Patterns Creational]]

## Singleton
Das Singleton ist eines der beliebtesten und meistgenutztesten Design Patterns in Programmen heutzutage.

Merkmale:
- Single Instance
	- Es gibt nur eine Instanz des Objektes
- Global Access
	- Das Objekt kann vom gesamten Programm referenziert werden (über statische public Methoden0)
- Lazy Loading
	- Objekte werden erst instanziiert, wenn sie gebraucht werden

## Prototype
Das Prototype Pattern wird vor allem für Klonvorgänge genutzt, bei der der Client die geklonte Klasse womöglich nicht kennt, sondern nur ein Interface (das die Zielklasse implementiert).

Merkmale:
- Existierende Objekte werden geklont
- Klonprozess wird delegiert (über Interface)
- Common Interface
- Genau eine "clone" Methode
- Private Felder können im Klonprozess mitkopiert werden

## Factory
Merkmale:
- Interface um Objekte zu erstellen
- Logik zum Erstellen der Objekte wird versteckt
- Aufruf einer speziellen Factory-Methode