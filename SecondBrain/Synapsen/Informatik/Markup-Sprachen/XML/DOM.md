
- steht für das *Document Object Model*
- Standard um auf Dokumente zuzugreifen und sie zu manipulieren

## Mehrere Arten
- HTML DOM
```html
<button type="button"  
onclick="document.getElementById('demo').innerHTML = 'Hello World!'">Click Me!  
</button>
```

- XML DOM
```javascript
txt = xmlDoc.getElementsByTagName("title")[0].childNodes[0].nodeValue;
```