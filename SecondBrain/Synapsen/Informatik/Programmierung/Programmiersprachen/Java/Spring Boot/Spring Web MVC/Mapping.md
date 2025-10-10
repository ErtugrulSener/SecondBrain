# Mapping

Die Request von Usern müssen irgendwie auf die Methoden im Backend in den [[Stereotypes#3) @Controller|Controllern]] gemappt werden. Dafür nutzen wir, sie so üblich, wieder Annotationen.

## @RequestMapping
Diese Annotation hat "method = RequestMethod.GET" als default Wert und akzeptiert als Value den Namen der Restschnittstelle. Beispiele:

- /loadform
- /user/{user_id}
- /{net_id}/user/{user_id}

## @GetMapping
Diese Annotation ist für Get Requests und akzeptiert keine Methode wie [[#@RequestMapping]] sondern nur den Pfad.

## @PostMapping
Selbes Spiel wie [[#@GetMapping]] nur für Post Requests. Für gewöhnlich werden mit @PostMapping Daten (in Form von JSON) an den Server gesendet, das Framework Spring WebMVC serialisiert das dann für das Backend in eine [[Java Bean]] und macht es der Methode verfügbar. Dafür gibt es bei den unterschiedlichen Frameworks verschiedene Methoden.

## @PathVariable
Damit kann man Variablen im Pfad referenzieren und in Java-Datentypen konvertieren. Beispiel:

```java
@RestController
class UserController {

  @GetMapping("/users/{userId}")
  String getSomething(@PathVariable("userId") Integer userId) {
	return "default";
  }

}
```

## @RequestParam
Query Parameter im GET-Request
Mit *required=false* könnte man auch nicht benötigte Felder angeben, die dann null sind, falls nicht im Request angegeben.

```java
@RestController
class UserController {
  // Aufgerufen mit: /users?userId=1234
  @GetMapping("/users")
  String getSomething(@RequestParam("userId") Integer userId) {
	return "default";
  }
}
```

## @RequestHeader
Einen Header im Request als Argument in Controller-Methode injezieren

```java
String getSomething(@RequestHeader("user-agent") String agent) {

}
```