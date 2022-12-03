Bei einem Merge vergleicht Git die Changesets aus zwei Commits uns versucht, die Änderungen zu kombinieren.

## Block/Chunk vs. Zeilen-Vergleich
Wie genau dieses "Kombinieren" geschieht ist Implementationsdetail und hängt vom benutzten Git-Tooling ab.

## Zeilen-Vergleich
Beim dieser Methode schaut sich Git im Changeset jede veränderte / gelöschte Zeile einer Datei an, sucht diese im Target-Branch und versucht diese Änderung dort anzuwenden. Stellt git nun fest, das die gleiche Zeile nicht mehr die selbe ist, wie sie im Source Branch war, gibt es einen Merge-Konflikt.

Oder kurz:

Branch *A* und Branch *B*
werden germerged in Branch *Main*.

Stellt git fest, dass die Änderung in Zeile 7 in Branch *A* nicht auf Branch *B* angewendet werden kann (z.B: weil diese Zeile abweicht von *Main*), dann gibt es den Merge-Konflikt.

## Block/Chunk-Vergleich
Man arbeitet mit Chunks und vergleichen von Chunks statt einzelnen Zeilen. Wie genau ist Implementationsdetail.