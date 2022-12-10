![[Die 3 Basistypen#Behavioral Patterns Behavioral]]

## Command
Der Client ruft eine Klasse A auf und übergibt ihm die benötigten Parameter in einem eigenen Objekt. Die Klasse A nutzt dieses "benötigte Interface" um damit eine Klasse B aufzurufen.

Die Commandklasse A dient als Delegator, weil der Client Klasse B nicht kennt.

## Mediator
Ein Objekt das zwischen zwei Objekten platziert wird und die Kommunikation zwischen ihnen übernimmt.

## Iterator
Funktioniert mit Collections, es wird spezifiziert welche Operationen man auf High Level für diese Collections können sollte.

## Memento
Wird für Save & Restore Funktionalitäten genutzt.

## Observer
Definiert Kommunikation zwischen Objekten, der Observable informiert die Observer bei einem eingehenden Event. 