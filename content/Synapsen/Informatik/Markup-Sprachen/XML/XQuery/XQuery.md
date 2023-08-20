- Abfragesprache für XML
- baut auf [[XPath]] auf
- ist eine Empfehlung des W3C seit 2007

## Beispiel
```xquery
for $x in doc("books.xml")/bookstore/book  
where $x/price>30  
order by $x/title  
return $x/title
```