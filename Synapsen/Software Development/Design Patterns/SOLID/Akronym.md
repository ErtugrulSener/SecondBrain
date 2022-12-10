Ursprünglich stammen diese Prinzipien von *Robert C. Martin* und sie stellen einen Guide da, wie man Applikationen bzw. Klassen bauen sollte.

# S - [[Single Responsiblity Principle]]
Eine Klasse sollte nur einen Job haben.

# O - [[Open Closed Principle]]
Klassen sollten offen für Erweiterungen sein, aber geschlossen für Modifikationen. Ergo man sollte eine Klasse verwenden können, ohne die Interna der Klasse verändern zu müssen.

# L - [[Liskov Substitution Principle]]
Überall wo eine Parent (Basis)-Klasse genutzt werden kann, sollte man auch eine Child (Kind)-Klasse nutzen können.

# I - [[Interface Seggregation Principle]]
Eine Klasse sollte nie gezwungen sein, ein Interface zu implementieren das nicht benutzt werden kann. Es werden (in anderen Worten) also nur Methoden der Klasse im Interface definiert, die für den Client relevant sind. 

# D - [[Dependency Inversion Principle]]
High-Level-Modules sollten nicht abhängig von Low-Level-Modules sein.