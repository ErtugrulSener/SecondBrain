# Data Fetcher
```ad-note
Alle Codebeispiele (und weitere) können auch detailliert hier gefunden werden: [Codebeispiele von Netflix](https://netflix.github.io/dgs/) 
```

## Beispielschema für folgende Beispiele
```GraphQL
type Query {
	shows: [Show]
}

type Show {
	title: String
	reviews: [Review]
}

type Review {
	starScore: Int
}
```

## @DgsComponent - Eine DataFetcher-Klasse definieren
```Java
@DgsComponent
public class ShowsDatafetcher {
	[...]
}
```

## @DgsQuery - Eine Query implizit definieren
```Java
@DgsComponent
public class ShowsDatafetcher {
    @DgsQuery
    public List<Show> shows() {
		[...]
    }
}
```

```ad-note
Hierbei wird der Funktionsname "shows" als Feldname genommen.
Der default parent type ist "Query", daher wird er hier nicht angegeben für @DgsQuery.
```

## @DgsData - Eine Query explizit definieren
```Java
@DgsComponent
public class ShowsDatafetcher {
    @DgsData(parentType = "Show", field = "reviews")
    public List<Show> shows() {
		[...]
    }
}
```

## @InputArgument - Einen Input annehmen
```Java
@DgsComponent
public class ShowsDatafetcher {
    @DgsQuery
    public List<Show> shows(@InputArgument input) {
		[...]
    }
}
```