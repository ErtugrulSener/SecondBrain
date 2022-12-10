Beim Befolgen dieses Prinzips ergeben sich folgende Vorteile:

- Multiple spezifische Interfaces (keine allgemeinen sondern kontextbezogene Interfaces)
- Weniger starke Kupplung und Code, der leichter zu refactoren ist
- Seiteneffekte und unerwünschte Konsequenzen verhindern (Weil sonst ableitende Klassen Methoden der Basisklasse nutzen, die für sie semantisch nicht funktionieren)