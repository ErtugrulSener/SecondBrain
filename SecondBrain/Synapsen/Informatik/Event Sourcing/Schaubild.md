![[CQRS and EventSourcing with Spring & Axon - Nakul Mishra 11-45 screenshot.png]]

## Beispiel
- Ein Command geht ein: "Der User sagt, er möchte 500€ abheben"
- Ein Event wird publiziert
- Das Event landet im Event Store
- Die Projection erhält das Event und die UI wird aktualisiert
- Es können mehrere Projektionen auf dieses Event lauschen, ergo mehrere UI's können durch einen Command dynamisch (also zur Laufzeit) aktualisiert werden