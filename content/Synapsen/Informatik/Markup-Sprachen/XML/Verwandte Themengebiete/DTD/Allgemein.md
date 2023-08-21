- steht für *Document Type Definition*
- beschreibt die Struktur und die validen Elemente sowie Attribute eines XML Dokumentes

## Beispiel 1: Simples DTD zur Validierung
```xml
<?xml version="1.0" encoding="UTF-8"?>  
<!DOCTYPE note SYSTEM "Note.dtd">  
<note>  
<to>Tove</to>  
<from>Jani</from>  
<heading>Reminder</heading>  
<body>Don't forget me this weekend!</body>  
</note>
```

```dtd
<!DOCTYPE note  
[  
<!ELEMENT note (to,from,heading,body)>  
<!ELEMENT to (#PCDATA)>  
<!ELEMENT from (#PCDATA)>  
<!ELEMENT heading (#PCDATA)>  
<!ELEMENT body (#PCDATA)>  
]>
```

```ad-note
#PCDATA steht für "parseable character data"
```

## Beispiel 2: Entity Referenzen definieren
```dtd
<!DOCTYPE note [  
<!ENTITY nbsp "&#xA0;">  
<!ENTITY writer "Writer: Donald Duck.">  
<!ENTITY copyright "Copyright: W3Schools.">  
]>
```

## Nutzung von DTD's
- Wenn unterschiedliche Gruppen einen Standard brauchen um Daten auszutauschen
- So kann man als Empfänger validieren, dass die empfangenen Daten auch valide sind
- Außerdem kann der Sender seine eigenen Daten validieren