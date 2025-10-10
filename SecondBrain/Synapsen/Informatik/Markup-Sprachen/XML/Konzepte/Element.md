- Ein Element ist alles inklusive dem Start-Tag sowie dem End-Tag

```xml
<price>29.99</price>
```

## Mögliche Bestandteile eines Elementes
- Text
- Attribute
- Andere Elemente

## Leere Elemente
```xml
<element></element>

ODER

<element />
```

## Regeln für Element-Namen
- sind Case-sensitive (Groß und Kleinschreibung ist wichtig!)
- müssen mit einem Buchstaben oder einem Unterstrich anfangen
- können nicht mit xml starten (XmL, xml, XML usw.)
- dürfen keine Leerzeichen enthalten

## Namenskonventionen
| Style       | Example      | Description                                                                        |
| ----------- | ------------ | ---------------------------------------------------------------------------------- |
| Lower case  | `<firstname>`  | All letters lower case                                                             | 
| Upper case  | `<FIRSTNAME>`  | All letters upper case                                                |
| Snake case  | `<first_name>` | Underscore separates words (commonly used in SQL databases)                        |
| Pascal case | `<FirstName>`  | Uppercase first letter in each word (commonly used by C programmers)               |
| Camel case  | `<firstName>`  | Uppercase first letter in each word except the first (commonly used in JavaScript) |