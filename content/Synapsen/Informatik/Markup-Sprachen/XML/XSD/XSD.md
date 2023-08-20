- Beschreibt, so wie ein [[DTD]] die Struktur eines XML-Dokumentes
- ist eine Alternative dazu
- sind mächtiger als DTD's
- unterstützen Datentypen und Namespaces

## Beispiel
```XSL
<xs:element name="note">  
  
<xs:complexType>  
  <xs:sequence>  
    <xs:element name="to" type="xs:string"/>  
    <xs:element name="from" type="xs:string"/>  
    <xs:element name="heading" type="xs:string"/>  
    <xs:element name="body" type="xs:string"/>  
  </xs:sequence>  
</xs:complexType>  
  
</xs:element>
```

## Gründe zur Nutzung
Die selben Gründe wie für DTD's:

![[DTD#Nutzung von DTD's]]