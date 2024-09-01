*Beispieltabelle:*

| Name     | Alter |
| -------- | ----- |
| Ertugrul | 24    | 

*Unique-Constraints:*
- Name, Alter (sind als Pärchen UNIQUE)

## *A*tomic
- All-Or-Nothing Operationen
	- Entweder alle Änderungen werden durchgeführt oder keine
- Das ist effizienter, man baut nur eine Verbindung auf und räumt sie nur 1 mal am Ende weg

z.B:
- Zeile 1 wird eingefügt (Lisa, 15)
- Zeile 2 wird eingefügt (Herbert, 16)
- Zeile 3 wird versucht einzufügen (Lisa, 15), bricht aber mit einem Unique Constraint (Es darf nur einen Menschen mit dem selben Alter in der Tabelle geben)

-> Zeile 1, 2 und 3 werden per Rollback rückgängig gemacht

## *C*onsistent
- Datenbank Contraints werden nicht gebrochen
- Die Daten sind konsistent vor und nach einer Änderung

z.B:
- Zeile 1 wird eingefügt (Ertugrul, 24)
- Zeile 1 wird rückgängig gemacht, der Unique Constraint 1 wurde nicht eingehalten

## *I*solated
- Die Transaktionen sind voneinander isoliert
- Kein Prozess oder eine andere Transaktion kann die Daten ändern, während eine Transaktion läuft

z.B:
- Transaktion A fügt Zeile 1 ein
- Transaktion B will auf Zeile 1 zugreifen
- Transaktion B findet Zeile 1 nicht

## *D*urable
- Änderungen, die commited sind, sind permanent
- Änderungen werden persistiert, auch bei einem Systemcrash

z.B:
- Transaktion A fügt eine Zeile hinzu, dabei crasht die Datenbank
- Falls Transaktion A noch nicht committed hat, ist nichts passiert
- Falls Transaktion A bereits committed hat, führt die Datenbank die Änderungen beim nächsten Start aus, sie dürfen nicht verloren gehen!