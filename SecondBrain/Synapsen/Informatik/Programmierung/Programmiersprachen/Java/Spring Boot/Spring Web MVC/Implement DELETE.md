## Hard vs. Soft Delete
Diese Entscheidung bestimmt, ob wir Einträge wirklich löschen oder nur als gelöscht markieren wollen.

## Audit Trail vs. Audit Fields
*Audit Fields* sind Felder wie *deleted* (boolean), *deleted_by* (die ID des Admins, der den User gelöscht hat) oder *delete_time* (Datetime).

*Audit Trail* ist ein Feld, das eine Art *History* über alle Operationen speichert, die man an einem Objekt vorgenommen hat.