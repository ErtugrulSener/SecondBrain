- steht für die *XML Path Language*
- Element des [[Synapsen/Informatik/Markup-Sprachen/XML/Verwandte Themengebiete/XSLT/Allgemein|XSLT]]-Standards
- Kann benutzt werden, um durch XML Dokumente zu navigieren (speziell durch die XML Elemente und ihre Attribute)
- XPath ist eine W3C Empfehlung

## Allgemein
- ist eine Syntax um Zeile von einem XML Dokument zu definieren
- nutzt Path Ausdrücke um durch XML Dokumente zu navigieren
- hat eine Bibliothek aus Standardfunktionen
- ist eines der Hauptelemente von [[Synapsen/Informatik/Markup-Sprachen/XML/Verwandte Themengebiete/XQuery/Allgemein]] und [[Synapsen/Informatik/Markup-Sprachen/XML/Verwandte Themengebiete/XSLT/Allgemein]]
- ist eine *W3c* Empfehlung

## Mögliche Rückgabewerte für Ausdrücke
- node-set
- string
- Boolean
- number

## Einige Ausdrücke
| Ausdruck                           | Beschreibung                                                                                                                           | 
| ---------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| /bookstore/book[1]                 | Selects the first book element that is the child of the bookstore element                                                              |
| /bookstore/book[last()]            | Selects the last book element that is the child of the bookstore element                                                               |
| /bookstore/book[last()-1]          | Selects the last but one book element that is the child of the bookstore element                                                       |
| /bookstore/book[position()<3]      | Selects the first two book elements that are children of the bookstore element                                                         |
| //title[@lang]                     | Selects all the title elements that have an attribute named lang                                                                       |
| //title[@lang='en']                | Selects all the title elements that have a "lang" attribute with a value of "en"                                                       |
| /bookstore/book[price>35.00]       | Selects all the book elements of the bookstore element that have a price element with a value greater than 35.00                       |
| /bookstore/book[price>35.00]/title | Selects all the title elements of the book elements of the bookstore element that have a price element with a value greater than 35.00 |