| Expression | Description                                                                                           |
| ---------- | ----------------------------------------------------------------------------------------------------- |
| nodename   | Selects all nodes with the name "nodename"                                                            |
| /          | Selects from the root node                                                                            |
| //         | Selects nodes in the document from the current node that match the selection no matter where they are |
| .          | Selects the current node                                                                              |
| ..         | Selects the parent of the current node                                                                |
| @          | Selects attributes                                                                                    | 

## Mehrere Pfade selektieren
| Path Expression                  | Result                                                        |
| -------------------------------- | ------------------------------------------------------------- |
| //book/title \| //book/price     | Selects all the title AND price elements of all book elements | 
| //title \| //price               | Selects all the title AND price elements in the document      |
| /bookstore/book/title \| //price | Selects all the title elements of t                           |

## Beispiel Ausdrücke
| Path Expression | Result                                                                                                                                         |
| --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| bookstore       | Selects all nodes with the name "bookstore"                                                                                                    |
| /bookstore      | Selects the root element bookstore<br><br>**Note:** If the path starts with a slash ( / ) it always represents an absolute path to an element! |
| bookstore/book  | Selects all book elements that are children of bookstore                                                                                       |
| //book          | Selects all book elements no matter where they are in the document                                                                             |
| bookstore//book | Selects all book elements that are descendant of the bookstore element, no matter where they are under the bookstore element                   |
| //@lang         | Selects all attributes that are named lang                                                                                                     |

