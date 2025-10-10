## Secure by default
Alle Endpoints sind per default "sicher", um eine Klasse explizit "für alle erreichbar zu machen" muss man sie mit

```Java
@AnonymousAllowed
```

annotieren. Beispiel:

```Java
@Endpoint  
@AnonymousAllowed  
public class HelloWorldEndpoint {  
}
```

## "Asynchronous" and "Non-blocking" communication
Die Kommunikation zwischen Backend und Fronted ist standartmäßig asynchron und nicht blockierend.

## BFF - Backend for Frontend
Das Backend liefert für jedes Frontend genau die Daten, die es benötigt. Sie sie sind stark aneinander gekoppelt.

## Build-In Webkomponenten
Hilla kommt mit einigen Built-In Webkomponenten, die man folgendermaßen importieren kann:

```Typescript
import '@vaadin/text-field'  
import '@vaadin/number-field'
import '@vaadin/number-button'
import '@vaadin/number-grid'
```

# Nachteile
## Backend muss Java sein
Aktuell wird der Java Code geparst, um die Endpoints für Typescript zu generieren - Kein Byte Code!

Das bedeutet, dass bisher als Backend die Sprache Java festgelegt ist, in Zukunft soll hier aber durch parsen von Bytecode und manuellem überführen der Java Docs eine Kompatabilität für alle JVM Sprachen geschaffen werden.