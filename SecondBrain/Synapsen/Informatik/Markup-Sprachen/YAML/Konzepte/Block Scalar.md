Mehrere Zeilen lassen sich als Block darstellen. Das geht auf zwei unterschiedlichen Wegen.

## Literal Block Scalar - |
Der Literal Block Scalar wird den Text genau so darstellen, wie man ihn sieht. Das heißt, dass Line-Breaks (\\n) berücksichtigt werden.

```YAML
include_newlines: |
  exactly as you see
  will appear these three
  lines of poetry
```

## Folded Block Scalar - \>
Der Folded Block Scalar interpretiert Line-Breaks (\\n) als Leerzeichen. Es entsteht also ein Satz. Man nutzt den Folded Block Scalar vor allem für die Lesbarkeit von Texten.

```YAML
fold_newlines: >
  this is really a
  single line of text
  despite appearances
```