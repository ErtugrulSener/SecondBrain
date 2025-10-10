Mit XPath selektiert man einen oder mehrere Knoten (Nodes) in einem XML-Dokument.

## 7 Arten von Nodes
- Element
- Attribut
- Text
- Namespace
- Processing-Instruction
- Kommentar
- Root-Node

## Beispiel XML
```xml
<?xml version="1.0" encoding="UTF-8"?>  
  
<bookstore>  
  <book>  
    <title lang="en">Harry Potter</title>  
    <author>J K. Rowling</author>  
    <year>2005</year>  
    <price>29.99</price>  
  </book>  
</bookstore>
```

## Atomic Values
- sind Nodes ohne Kinder oder Eltern

```xml
J K. Rowling  
  
"en"
```

## Items
- sind [[Nodes#Atomic Values]] oder Nodes.