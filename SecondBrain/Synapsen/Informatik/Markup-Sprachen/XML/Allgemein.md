## XML - eXtensible Markup Language
- wurde designed um Daten zu speichern sowie um Daten zu transporieren
- Markup-Sprache wie z.B: auch [[Tools]] oder [[HTML]]
- ist lesbar für Menschen und Maschinen
- Empfehlung des *W3C* Februar 1998
- Unabhängig von Programmiersprachen, Frameworks, Betriebssystemen und Hardware

## Beispiel
```xml
<?xml version="1.0" encoding="UTF-8"?>
<note>
  <from>Jani</from>
  <to>Tove</to>
  <heading>Reminder</heading>
  <body>Don't forget me this weekend!</body>
</note>
```

## XML vs. HTML
- XML wurde designed um Daten zu speichern (*WAS* Daten sind)
- HTML um Daten anzuzeigen (*WIE* Daten aussehen)
- XML-Tags sind nicht vorher festgelegt wie bei HTML z.B: das `<b>`-Tag

## Verschiedene festgelegte XML Standards
### Beispiel: XMLNews
```xml
<?xml version="1.0" encoding="UTF-8**"**?>  
<nitf>  
  <head>  
    <title>Colombia Earthquake</title>  
  </head>  
  <body>  
    <headline>  
      <hl1>143 Dead in Colombia Earthquake</hl1>  
    </headline>  
    <byline>  
      <bytag>By Jared Kotler, Associated Press Writer</bytag>  
    </byline>  
    <dateline>  
      <location>Bogota, Colombia</location>  
      <date>Monday January 25 1999 7:28 ET</date>  
    </dateline>  
  </body>  
</nitf>
```

Weitere Beispiele:
- Stocks and Shares
- Financial transactions
- Medical data
- Mathematical data
- Scientific measurements
- Weather services