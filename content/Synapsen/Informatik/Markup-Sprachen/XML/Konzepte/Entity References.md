Es gibt spezielle Character in XML wie *\<*.

Um diese auszudrücken nutzt man *Entity Referenzen*

```xml
<message>salary &lt; 1000</message>
```

## 5 Entity Referenzen
| Entity Referenz | Zeichen | Beschreibung   |
| --------------- | ------- | -------------- |
| `&lt;`          | <       | less than      |
| `&gt;`          | >       | greater than   |
| `&amp;`         | &       | ampersand      |
| `&apos;`        | '       | apostrophe     |
| `&quot;`        | "       | quotation mark |

Strikt verboten sind aber nur:
- `<`
- `&`

Es ist aber Best Practice für alle diese Zeichen Entity Referenzen zu nutzen.