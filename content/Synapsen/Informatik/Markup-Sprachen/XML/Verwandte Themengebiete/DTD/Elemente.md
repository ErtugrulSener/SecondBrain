- werden mit folgender Syntax deklariert

```xml
<!ELEMENT element-name category>

ODER

<!ELEMENT element-name (element-content)>
```

## Leere Elemente
- werden mit dem Stichwort EMPTY als *element-content* markiert

```xml
<!ELEMENT element-name EMPTY>
```

in XML:
```xml
<element-name />
```

## Elemente mit PCDATA
```xml
<!ELEMENT element-name (#PCDATA)>
```

## Elemente mit ANY Content
```xml
<!ELEMENT element-name ANY>
```

## Elemente mit Kindern
```xml
<!ELEMENT element-name (child1, child2, child3)>
```

## Elemente mit mindestens einem Kind (+)
```xml
<!ELEMENT element-name (child+)>
```

## Elemente mit null oder mehr Kindern (\*)
```xml
<!ELEMENT element-name (child*)>
```

## Elemente mit null oder einem Kind (?)
```xml
<!ELEMENT element-name (child?)>
```

## Oder Konditionen in Elementen
```xml
<!ELEMENT element-name ((child1|child2))>
```

## Komplexeres Beispiel
```xml
<!ELEMENT note (#PCDATA|to|from|header|message)*>
```