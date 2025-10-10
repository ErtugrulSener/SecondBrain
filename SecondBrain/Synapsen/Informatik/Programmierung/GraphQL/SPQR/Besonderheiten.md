## Code-First Ansatz
Die erste offensichtliche Besonderheit ist, dass es (soweit mir bekannt) das einzige Java Framework für GraphQL ist, dass den Code-First Ansatz wählt.

Das heißt, dass man als Entwickler seine API gestaltet und nur mit dem Code arbeitet, das Schema wird dann aus der API automatisch generiert.

```ad-note
Frameworks wie neben DGS und Spring GraphQL nutzen den Schema-First Ansatz, dort wird das Schema vom Entwickler spezifiziert.

DGS hat einen Generator, der aus dem Schema die Entitäten erzeugt, die API müsste man weiterhin selbst pflegen / initial erstellen.
```

## Doch Schema-First?
Jaein. Das Schema welches wir bei diesem Framework bearbeiten ist unsere API. Es stimmt also wenn man sagt, dass kein GraphQL Schema manuelle erstellt und gepflegt werden muss.

Allerdings ist es im Prinzip weiterhin "Schema-First", nur das unser Schema nun in Java beschrieben wird. Man muss sich bewusst machen, was Rückgabetypen und Argumententypen für das erstellt GraphQL Schema am Ende bedeuten.

## Weitere technische Besonderheiten
- Benötigt für das Setup nur etwa 3 Zeilen Code
- Gute Integration mit [[Spring Boot]] (spring boot starter und autoconfigure Dependency ist vorhanden)
- Erweiterbar und konfigurierbar
- Wenige Dependencies