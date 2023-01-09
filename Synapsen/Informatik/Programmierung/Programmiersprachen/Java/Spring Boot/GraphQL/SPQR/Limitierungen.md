So gerne wir auch die [[Besonderheiten]] haben, muss man gewisse Dinge (Stand 29.12.2022) beachten:

## Innere (statische) Klassen
Eine Struktur (Alle Klassen in einer Javadatei) wie:

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

## Statische Felder werden nicht ignoriert
Aktuell werden statische Felder beim Serialisieren der Java Objekte durch das Framework mit beachtet, es gibt aber schon einen Pull Request dazu (zum Ignorieren von statischen Feldern).

## Spring Boot Version 2
Das Framework ist aktuell mit der Spring Boot Version 2 erstellt und damit kompatibel. Obwohl bei meinen Tests auch unter Spring Boot 3 das Ganze funktionierte, kann man es nicht guten Gewissens in Produktion empfehlen.

## Required Parameter (obwohl es in keiner Dokumentation steht), siehe [[Referenzen]]
Die Parameter

```properties
graphql.spqr.gui.target-endpoint = /graphql  
graphql.spqr.gui.target-ws-endpoint = /graphql-ws
```

müssen aus irgendeinem Grund beim Startup gesetzt werden, sonst gibt es eine NPE. Ich gehe zwar davon aus, dass dies in einer Zukunftsversion gefixt wird, aber bisher ist dies zu beachten.

## Prüfung aller Querys / Mutations auf einer Seite, statt nur der des aktuellen Requests
Auch wenn nur ein bestimmter Request gesendet wird, wird jede Mutation / Query auf dieser Seite auf "Vollständigkeit" bzw. "formale Korrektheit" geprüft, leider ist die Fehlermeldung hier recht schwierig zu verstehen.

Daher sollte man einfach Wissen, dass eine Seite mit folgendem Inhalt:

```GraphQL
mutation createA {
  createA(dto: {
      uuid: "1d460da2-571a-4b36-97a0-b7f4ddf184e9"
  }) {
    uuid
  }
}

mutation createB {
  createB(dto: {
    a: {
      uuid: ""
    }
  }) {
    uuid
  }
}
```

und dem Ausführen der Mutation ```createA``` einen Fehler gibt, dass:
```java.lang.UUID.fromString("")``` nicht erfolgreich war, ein leerer String ist kein gültiger UUID.

Auffällig ist, dass der leere String bei der Mutation ```createB``` drin ist, die ja überhaupt nicht ausgeführt wurde.

## Fehlende offizielle Dokumentation
Es gibt keine wirkliche Dokumentation zum Framework, zumindestens finde ich keine offizielle und die Github README zeigt nur die simpelsten Use Cases.