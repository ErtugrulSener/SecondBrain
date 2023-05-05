## Wichtige Punkte die aufkommen
- Security (Darf jeder User alle Einträge bei findAll-Aufrufen sehen?)
- Pagination (Darf der User unendlich viele Einträge sehen?)
- Order (Sollen die Ergebnisse irgendwie sortiert werden?)

## Sortierung empfohlen
Pagination ohne Sortierung sorgt für ein Problem:
Wenn ich eine neue Ressource hinzufüge, auf welcher Seite landet sie?

Richtig. Man kann es nicht wissen, ohne das man einen Request stellt und nachsieht, ob die Seite nun in dieser Page auftaucht.

Beispiel dafür mit Spring Data:

 ```java
Page<CashCard> page2 = cashCardRepository.findAll(
    PageRequest.of(
        1,  // page index for the second page - indexing starts at 0
        10, // page size (the last page might have fewer items)
        Sort.by(new Sort.Order(Sort.Direction.DESC, "amount"))));
```