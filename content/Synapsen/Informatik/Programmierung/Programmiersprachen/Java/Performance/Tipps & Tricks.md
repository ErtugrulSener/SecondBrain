## GC auf vom Netz genommenen Maschinen
100ms ist eine Maximalwartezeit für "Stateful Responsiveness" die laut Jack Shirazi (Java Developer, Talk von Devoxx) möglich ist. Dafür gibt es in der Produktion einen Trick:

1) Man stellt einige Maschinen auf.
2) Periodisch nimmt man eine Maschine aus dem Netz, forciert eine volle Garbage Collection (kann bis zu 20 Sekunden dauern).
3) Man fügt die Maschine wieder ins Netz hinzu und macht das Selbe mit der nächsten Maschine.

Auf diese Weise muss kein Endnutzer bei seinem Request warten, die Garbage Collection findet außerhalb des skalierten Netzes statt.

## Periodische GC
Ein anderer Weg, um die Garbage Collection zu umgehen ist es, einen sehr großen Heap zu wählen. z.B: 10GB und ein Mal täglich (in der Nacht) die Applikation neuzustarten. Es gibt keine Pause Times, weil der GC nicht aufräumen muss.

## Festplatte statt RAM
Manche sehr große Objekte gehören nicht unbedingt in den RAM, auch wenn der Zugriff darauf natürlich schneller ist. Es könnte sich manchmal lohnen, die Objekte auf die Festplatte zu schreiben und auf der Festplatte zu interagieren. Das hat auch den Vorteil, das man beim nächsten Mal "das Objekt" nicht neu laden muss.

Dies kann man noch verknüpfen mit einem lokalen "Caching", damit das Objekt nur neu initialisiert wird bei Änderung (z.B: am Änderungsdatum zu sehen).
