- wenn man unbekannte Nodes sucht, kann man Wildcards verwenden

| Wildcard                 | Description                  |
| ------------------------ | ---------------------------- |
| Matches any element node |                              |
| @                        | Matches any attribute node   |
| node()                   | Matches any node of any kind |

## Beispiele für Wildcards

| Path Expression | Result                                                                   |
| --------------- | ------------------------------------------------------------------------ |
| /bookstore/     | Selects all the child element nodes of the bookstore element             |
| //*             | Selects all elements in the document                                     |
| //title[@]      | Selects all title elements which have at least one attribute of any kind |
