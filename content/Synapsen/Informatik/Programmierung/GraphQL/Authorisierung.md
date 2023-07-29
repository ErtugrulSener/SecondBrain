## Wer darf bestimmte Felder ansprechen?
## Lösung 1: Direktiven
Eine Möglichkeit wäre es, Direktiven ins GraphQL Schema hinzuzufügen und im Code zu prüfen.

```GraphQL
type Project {
	code: String
	currentFunction: Long @auth(role: "Manager")
}
```

In SPQR könnte man eine Custom Annotation nutzen.

```Java
@GraphQLQuery
@Auth(role = "Manager")
public long mySecretFunction() {
	return 1337;
}
```

Die Prüfung wer was erreichen darf, müsste man in Runtime anhand der Annotation trotzdem selbst machen.

## Wer darf bestimmte Felder sehen?
Das ist eine ganz andere Frage. Alleine die Information, das da ein Feld ist (das protected ist) - Ist quasi eine Einladung für den Hacker.

## Lösung: GraphQLFieldVisibility