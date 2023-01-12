Manche Dinge werden mit GraphQL einfach härter, z.B: Anfragen des Kunden, die beliebig tiefgeschachtelt und komplex werden können.

## GraphQLComplexity
Ein Weg dem entgegenzuwirken ist es, für Funktionen zu spezifizieren wie komplex sie werden dürfen. Das Framework errechnet für die gesamte Query eine Komplexität und wenn die einen Treshhold übersteigt, dann lehnt der Server die Query ab, ohne die Resolver auszuführen.

```Java
@GraphQLQuery
@GraphQLComplexity("pageSize * childScore")
public List<Project> projects(int pageSize, int pageNumber) {
	return ...;
}
```

Dies spart enorm Performance.

## Tiefe limitieren
Github macht dies zum Beispiel, sie limitieren die Tiefe auf 10.

In GraphQL Java geht das folgendermaßen:

```Java
GraphQL runtime = GraphQLRuntime.newGraphQL(schema)
	.instrumentation(new MaxQueryDepthInstrumentation(10))
	.build();
```

## Ausführzeit limitieren
z.B: durch Applikationsserver oder Datenbankverbindung

## White List Queries
Wenn man alle Clienten kontrolliert, könnte man keine Querys akzeptieren sondern nur Hashes, die vom Server zu GraphQL Queries gemappt werden.

## Ergebnisse streamen
Anstatt den kompletten Request auf ein Mal zu resolven, kann man die Ergebnisse nacheinander an den Client geben. Das SPQR Framework arbeitet bereits an einer Lösung hierfür.