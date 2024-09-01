| AxisName           | Result                                                                                                                       |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------- |
| ancestor           | Selects all ancestors (parent, grandparent, etc.) of the current node                                                        |
| ancestor-or-self   | Selects all ancestors (parent, grandparent, etc.) of the current node and the current node itself                            |
| attribute          | Selects all attributes of the current node                                                                                   |
| child              | Selects all children of the current node                                                                                     |
| descendant         | Selects all descendants (children, grandchildren, etc.) of the current node                                                  |
| descendant-or-self | Selects all descendants (children, grandchildren, etc.) of the current node and the current node itself                      |
| following          | Selects everything in the document after the closing tag of the current node                                                 |
| following-sibling  | Selects all siblings after the current node                                                                                  |
| namespace          | Selects all namespace nodes of the current node                                                                              |
| parent             | Selects the parent of the current node                                                                                       |
| preceding          | Selects all nodes that appear before the current node in the document, except ancestors, attribute nodes and namespace nodes |
| preceding-sibling  | Selects all siblings before the current node                                                                                 |
| self               | Selects the current node                                                                                                     |

## Location Path Expression
```xml
axisname::nodetest[predicate]
```

## Beispiele für Location Paths
| Example                | Result                                                                                        |
| ---------------------- | --------------------------------------------------------------------------------------------- |
| child::book            | Selects all book nodes that are children of the current node                                  |
| attribute::lang        | Selects the lang attribute of the current node                                                |
| child::*               | Selects all element children of the current node                                              |
| attribute::*           | Selects all attributes of the current node                                                    |
| child::text()          | Selects all text node children of the current node                                            |
| child::node()          | Selects all children of the current node                                                      |
| descendant::book       | Selects all book descendants of the current node                                              |
| ancestor::book         | Selects all book ancestors of the current node                                                |
| ancestor-or-self::book | Selects all book ancestors of the current node - and the current as well if it is a book node |
| child::/child::price   | Selects all price grandchildren of the current node                                           |
