## Facade
![[facade-pattern.png]]

Die Facade-Klasse versteckt die Komplexität eines Systems vor dem Anwender (im Beispiel Subsystem C) von dem Client, indem sie Methoden zur Verfügung stellt, die mit den Klassen und mit den anderen Klassen zu interagieren.

Der Client kennt nur das Interface der Facade-Klasse und ruft die Methoden auf.

## Decorator
Beim Decorator Pattern wird ein Objekt in ein Wrapper Objekt eingepackt, das alle Funktionalitäten beinhält, die man benötigt. So kann ein Objekt Funktionalitäten nutzen.

Der große Vorteil dieses Patterns ist, dass man Kompositon benutzt statt Vererbung (starke Kopplung).

## Adapter
Das Adapter Pattern erlaubt es zwei miteinander inkompatiblen Klassen zusammenzuarbeiten, indem der Adapter eine Art "Middle-Man" spielt und sich eine Instanz der Zielklasse hält und dann ein Mapping der Methoden macht.

Merkmale sind:
- Inkompatible Interfaces
- Konvertieren von Interfaces
- Verstecken von Komplexitäten beim Konvertieren
- Zwei-Wege-Adapter

## Bridge
Das Bridge Pattern wir vorrangig verwendet, um die Abstraktion und die Implementation eines Moduls mit vielen Klassen zu trennen.

So ist es möglich, die Implementation zu verändern, ohne dass der Client etwas davon merkt bzw. eine Änderung vornehmen muss.