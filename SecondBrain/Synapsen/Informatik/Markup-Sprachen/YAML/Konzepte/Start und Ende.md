Drei Bindestriche *---* können am Anfang und Ende einer YAML Dateien stehen um den Anfang und das Ende zu signalisieren. Das ist ein Teil der YAML Spezifikation. Sie signalisieren "Einen neuen Abschnitt"

```YAML
---
# A list of tasty fruites
fruites:
  - Apple
  - Orange
  - Strawberry
  - Mango
---
other:
  - test
  - test
---
```