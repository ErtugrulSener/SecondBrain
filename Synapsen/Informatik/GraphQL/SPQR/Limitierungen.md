So gerne wir auch die [[Besonderheiten]] haben, muss man gewisse Dinge (Stand 29.12.2022) beachten:

## Innere (statische) Klassen
Eine Struktur wie:

```Java
class Member_1 {
	private int id;
}

class Member_2 {
	private int id;
}

public class Base {
	private Member_1 member_1;
	private Member_2 member_2;
}
```

kann beim GraphQL Request nicht aufgelöst werden und erzeugt folgende Fehlermeldung (DataFetchingException):

```Java
Exception while fetching data (/findPrayerTimesForCity/place/city) : class io.leangen.graphql.metadata.execution.MethodInvoker cannot access a member of class com.ertu.prayertimes.dtos.PlaceDTO with modifiers \"public\"
```

## Spring Boot Version 2
Das Framework ist aktuell mit der Spring Boot Version 2 erstellt und damit kompatibel. Obwohl bei meinen Tests auch unter Spring Boot 3 das Ganze funktionierte, kann man es nicht guten Gewissens in Produktion empfehlen.

