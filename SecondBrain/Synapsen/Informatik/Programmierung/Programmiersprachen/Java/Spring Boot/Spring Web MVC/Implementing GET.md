## Warum nutzen wir die @RestController Annotation?
Die eigentliche Frage ist ja:
*Warum müssen unsere Rest Controller auch Spring Beans sein?**

Die Antwort liegt eigentlich auf der Hand: *Spring muss diese Beans im Spring Web "Framework" injizieren können*, um die eigehenden Requests auf die korrekte Methode innerhalb der Controllers weiterleiten zu können. Dadurch, das wir unseren Controller so annotieren, machen wir ihn dem Spring Web Framework quasi "bekannt".

## Häufig genutzte Annotationen
- @RestController
- @RequestMapping (Die allgemeine Mapping Methode)
	- @GetMapping
	- @PostMapping
	- @PutMapping
	- @DeleteMapping
- @PathVariable

## Häufig genutzte Klassen
### ResponseEntity
Als Rückgabewert für Controller, sie hat so Hilfsfunktionen wie ResponseEntity.ok(...) usw.

```Java
@RestController
public class CashCardController {
  @GetMapping("/cashcards/{requestedId}")
  public ResponseEntity<CashCard> findById(@PathVariable Long requestedId) {
     CashCard cashCard = /* Here would be the code to retrieve the CashCard */;
     return ResponseEntity.ok(cashCard);
  }
}
```