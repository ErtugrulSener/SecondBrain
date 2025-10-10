# Allgemein
- Das DGS im Titel steht für Domain Graph Service
- Es war zunächst ein intern genutztes Framework von Netflix
- Released wurde es in 2020

# Vorteile DGS-Framework \<-\> GraphQL Java
1) Das DGS Framework ist einfacher in der Handhabung und für neuere Developer leichter zu verstehen (GraphQL-Java ist eher low level).
3) Netflix nutzt das DGS-Framework intern (mit Ausnahme von etwa 3 Securitymodulen, die nicht open sourced wurden) selbst, das macht es vertrauenswürdiger.
4) Das Framework ist super dokumentiert.
5) Die Integration des Frameworks mit IntelliJ ist einfach genial. Es gibt einen schönen Reiter, wo man die Javaklassen (Resolver) gefiltert sehen kann! Siehe hier:

![[intellij-integration.png]]

# Warum startet das DGS-Framework mit Version 3.X?
- Netflix hat das Framework intern benutzt und bereits einige Releases gemacht
- Als sie open sourcen wollten, haben sie die Git History gelöscht und die Version einfach beibehalten (vermutlich weils sonst intern zu Kollisionen gekommen wäre)

# Referenzen
[Zur Dokumentation](https://netflix.github.io/dgs/getting-started/)