## Wer sollte eine ID erstellen, der Server oder der User?
Die Wahrheit ist: REST ist kein Standard, es ist eher ein Weg HTTP für Datenoperationen zu nutzen. REST enthält eine Anzahl von Richtlinien, doch die Antwort auf diese Frage liegt beim *API-Designer*!

## Idempotenz und HTTP
Idempotenz (im Informatik-Kontext) ist, wenn der Aufruf einer Methode mit dem selben Input auch zum selben Output führt, egal wie häufig dies geschieht.

Laut HTTP Protokoll sind folgende Methoden idempotent:
- GET
- PUT
- DELETE

und folgende nicht:
- POST
- PATCH

## Location Header für Create-Response
Das HTTP Protokoll sieht vor, dass bei einem erfolgreichen erstellen einer Ressource der Header "Location" die URI zur erstellen Ressource trägt.

Beispiel:
-   Status Code: `201 CREATED`
-   Header: `Location=/cashcards/42`

## ResponseEntity.created(...)
Um das nicht explizit machen zu müssen mit:

```Java
return ResponseEntity
		.status(HttpStatus.CREATED)
		.header(HttpHeaders.LOCATION, uriOfCashCard.toASCIIString())
		.build();
```

nutzen wir die ResponseEntity::created Methode von Spring:

```Java
return ResponseEntity
		.created(uriOfCashCard)
		.build();
```