## Prüfen ob ein Wert des Elementes mit einem Substring anfängt
```xml
/persons/person[starts-with(@firstName, 'H')]
```

## Prüfen ob ein Attribut-Wert maximal 5 Zeichen lang ist
```xml
/persons/person[string-length(@firstName) <= 5]
```

## Summe aller Zahlen, die gerundet 34 ergeben
```xml
sum(/numbers/number[round(text()) = 34])
```

## Alle Links in einem Dokument zu einem bestimmten Namensraum finden
```xml
/document/content//x:a
```

## Alle Links in einem Dokument zu einem bestimmten Namensraum, wenn sie einen Substring beinhalten
```xml
/document/content//x:a[contains(@href, 'google')]
```

## Alle Nodes die mit 'item' anfangen
```xml
/document/*[starts-with(name(), 'item')]
```