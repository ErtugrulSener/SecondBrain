Die simpelste Form von Werten in YAML sind "Key-Value-Pairs" wie das Folgende:

```YAML
openapi: 3.0.3
```

## Besonderheit in Keys
### Unique
Die Schlüssel sind unique, wie in Map / Dictionieres anderer Sprachen auch.

### Leerzeichen
Obwohl viele Programmiersprachen dies nicht in ihren Variablennamen erlauben, können YAML Keys auch Leerzeichen enthalten!

```YAML
first Name: Ertu
```

### Quotes
Auch erlaubt sind Anführungsstriche

``` YAML
'first': Hi
"second": Hii
```

```ad-note
Grundsätzlich sollte man die Anführungsstriche "" (double-quotes) nur nutzen, wenn der Key einen Character besitzt, den man escapen muss.
```