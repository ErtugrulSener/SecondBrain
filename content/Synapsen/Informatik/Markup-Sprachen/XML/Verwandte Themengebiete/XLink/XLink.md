- wird genutzt um Hyperlinks zwischen XML Dokumenten herzustellen
- Jedes XML Dokument kann als ein Link sein
- XLink ist eine W3C Empfehlung

## Beispiel
```xml
<?xml version="1.0" encoding="UTF-8"?>  
  
<homepages xmlns:xlink="http://www.w3.org/1999/xlink">  
  <homepage xlink:type="simple" xlink:href="https://www.w3schools.com">Visit W3Schools</homepage>  
  <homepage xlink:type="simple" xlink:href="http://www.w3.org">Visit W3C</homepage>  
</homepages>
```