## Prüfen ob ein Wert des Elementes mit einem Substring anfängt
```xml
/persons/person[starts-with (@firstName, 'H')]
```

## Prüfen ob ein Attribut-Wert maximal 5 Zeichen lang ist
```xml
/persons/person[string-length(@firstName) <= 5]
```

## Summe aller Zahlen, die gerundet 34 ergeben
```xml
sum(/numbers/number[round(text()) = 34])
```