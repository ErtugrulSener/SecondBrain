- werden wie folgt deklariert

```xml
<!ATTLIST element-name attribute-name attribute-type attribute-value>
```

## Beispiel für simples Attribut mit default Wert
```xml
<!ATTLIST payment type CDATA "check">
```

## Beispiel für Attribut mit fixem Wert
```xml
<!ATTLIST sender company CDATA #FIXED "Microsoft">
```

## Beispiel für enumerierte Werte
```xml
<!ATTLIST payment type (check|cash) "cash">
```

## Mögliche Attributtypen (attribute-type)
| Type         | Description                                   |
| ------------ | --------------------------------------------- |
| CDATA        | The value is character data                   |
| (en1 \| en2) | The value must be one from an enumerated list |
| ID           | The value is a unique id                      |
| IDREF        | The value is the id of another element        |
| IDREFS       | The value is a list of other ids              |
| NMTOKEN      | The value is a valid XML name                 |
| NMTOKENS     | The value is a list of valid XML names        |
| ENTITY       | The value is an entity                        |
| ENTITIES     | The value is a list of entities               |
| NOTATION     | The value is a name of a notation             |
| xml:         | The value is a predefined xml value           |

## Mögliche Attributwerte (attribute-value)
| Value          | Explanation                        |
| -------------- | ---------------------------------- |
| value          | The default value of the attribute |
| #REQUIRED      | The attribute is required          |
| #IMPLIED       | The attribute is optional          |
| #FIXED _value_ | The attribute value is fixed       |