- können intern und extern definiert werden

## Syntax
```xml
<!ENTITY entity-name "entity-value">
```

## Beispiel für interne Entity
```xml
<!ENTITY writer "Donald Duck.">
```

- Nutzung davon im XML
```xml
<author>&writer;</author>
```

## Beispiel für externe Entity
```xml
<!ENTITY entity-name SYSTEM "URI/URL">
```