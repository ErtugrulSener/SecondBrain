- Verhindern von Namenskonflikten

- Beispiel
```xml
<h:table xmlns:h="http://www.w3.org/TR/html4/">
  <h:tr>  
    <h:td>Apples</h:td>  
    <h:td>Bananas</h:td>  
  </h:tr>  
</h:table>  

<f:table xmlns:f="https://www.w3schools.com/furniture">
  <f:name>African Coffee Table</f:name>  
  <f:width>80</f:width>  
  <f:length>120</f:length>  
</f:table>
```
- Alle Kinder-Elemente unter dem Namespace kriegen auch den Namespace, wenn sie den selben Präfix haben (h oder f im Beispiel)
- Man kann den Präfix auch weglassen

## URI im Namespace?
- Hat keine Besondere Beduetung, sollte nur unique sein
- Firmen nutzen das, um auf eine Seite weiterzuleiten, bei der alle URI's erklärt werden