- Jedes XML Dokument muss genau ein *Wurzelelement* haben

```xml
<?xml version="1.0" encoding="UTF-8**"**?>
<root>  <!-- Das Wurzelelement ist root -->
  <child>  
    <subchild>.....</subchild>  
  </child>  
</root>
```

- Jedes XML Element benötigt einen schließenden Tag

```xml
<a></ <!-- Das wäre z.B ungültig! -->
<br />
```

- XML Tags sind Case sensitiv

```xml
<Message>AAA</Message>
<message>aaa</message>
```

- Attribute in XML Elementen müssen Quotes haben
```xml
<note date="12/11/2007">  
  <to>Tove</to>  
  <from>Jani</from>  
</note>
```