![[Synapsen/Software Design/SOLID/Allgemein#S - Single Responsiblity Principle]]

Beim Befolgen dieses Prinzips entstehen sehr viele Klassen, mit ihrem eigenen Zweck. Das hat aber einige Vorteile:

- Die Klasse ist besser testbar (Man braucht weniger Testfälle pro Klasse)
- Weniger Funkionalität pro Klasse - Weniger Kopplung zu anderen Klassen
- Bessere Organisation innerhalb der Klasse
- Ein Fehler ist lokalisiert in einer kleinen Klasse statt in irgendeiner Methode in einer riesigen Klasse (was Debugging erschweren würde)

Aber das Wichtigste:
> *Kleinere Klassen lassen sich einfacher an verschiedenen Stellen des Programms nutzen, als eine riesige mächtige Klasse, die nur für einen ganz speziellen Anwendungsfall relevanz hätte.*