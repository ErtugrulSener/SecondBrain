![[Synapsen/Informatik/Software Design/Prinzipien/SOLID/Allgemein#I - Interface Seggregation Principle]]

Dieses Prinzip hat viele Ähnlichkeiten zum [[Single Responsiblity Principle]], nur das es sich auf Interfaces fokussiert.

Beim Befolgen dieses Prinzips ergeben sich folgende Vorteile:

- Multiple spezifische Interfaces (keine allgemeinen sondern kontextbezogene Interfaces)
- Weniger starke Kopplung und Code, der leichter zu refactoren ist
- Seiteneffekte und unerwünschte Konsequenzen verhindern (Weil sonst ableitende Klassen Methoden der Basisklasse nutzen, die für sie semantisch nicht funktionieren)