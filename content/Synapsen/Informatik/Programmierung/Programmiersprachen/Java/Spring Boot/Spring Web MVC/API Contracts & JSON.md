Wenn man eine API entwickelt, ergeben sich einige Fragen:
- Wie sollen die Klienten mit der API kommunizieren?
- Welche Daten müssen sie uns für welche Szenarien senden?
- Welche Daten muss die API zurücksenden und wann?
- Wie reagiert die API bei Fehleingaben und wie kommunizieren wir diese an den Client?

Wenn möglich, sollte es dafür absprachen geben, die klar zwischen Konsumenten & API abgesprochen sind. Das sind die sogenannten *Api Contracts*.

## Api Contracts
Beispiel:

```
Request
  URI: /cashcards/{id}
  HTTP Verb: GET
  Body: None

Response:
  HTTP Status:
    200 OK if the user is authorized and the Cash Card was successfully retrieved
    403 UNAUTHORIZED if the user is unauthenticated or unauthorized
    404 NOT FOUND if the user is authenticated and authorized but the Cash Card cannot be found
  Response Body Type: JSON
  Example Response Body:
    {
      "id": 99,
      "amount": 123.45
    }
```

## Warum sind API Contracts wichtig?
Sie sind so geschrieben, dass man sie einfach in Funktionalitäten vom Provider und Konsumenten übersetzen kann sowie automatisiert Tests generieren kann.

Wichtiger aber ist sie um zu das Verhalten einer REST API zu spezifizieren. Sie beschreiben wie Daten serialisiert und deserialisiert werden für jeden Parameter und Befehl einer Rest API.

## Was ist JSON?
JSON ist ein Akronym und steht für die ```JavaScript Object Notation```. Man nutzt dieses Format um Daten zwischen Systemen auszutauschen, die in einer spezifischen Form dargestellt werden. Diese Form kann man einfach lesen und verstehen.

Hier ist ein Beispiel:

```
{
	"id": 99,
	"amount": 123.45
}
```

Andere Formate sind:
- YAML (Yet Another Markup Language)
- XML (Extensible Markup Language)                                                                                                                                                                                                                                                                                                 