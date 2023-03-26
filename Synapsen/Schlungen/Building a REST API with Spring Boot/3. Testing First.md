## Test Driven Development
- wenn man zunächst die Tests schreibt und dann die eigentliche Business Logik
- wir spezifizieren das *erwartete Verhalten* an ein System statt uns am *vorhandenen Verhalten* zu orientieren (bessere API's für den Klienten entstehen z. B.)
- wenn die Tests durchlaufen, hat man funktionierenden Code und die Anforderung ist erfüllt, zukünftige Changes werden direkt geprüft

## Testing Pyramid
Die Tests einer Anwendung sind von unterschiedlicher Art. Folgend sind sie aufgebaut:

![[testing-pyramid.png]]

*Unit Tests*:
- Testen eine Einheit der Applikation, sind schnell auszuführen und es gibt potenziell viele davon

*Integration Tests*:
- Verschiedene Einheiten eines Systems werden hochgefahren, um die Interaktion zwischen Ihnen zu testen (z. B: Spring Boot Anwendung mit Mailserver und FTP-Ablage)
- schwieriger zu implementieren als Unit Tests

*E2E Tests*:
- sogenannte "End to End" Tests
- finden meist auf dem Browser statt, so als wäre man ein gewöhnlicher User der sich durch die Anwendung klickt
- sehr fragil, durch sich stetig ändernde UI's

## Red-Green-Refactor-Loop
1. Red: Schreibe einen fehlschlagenden Test für die Funktionalität
2. Green: Implementiere die simpelste Lösung, damit der Test durchläuft
3. Refactor: Schaue auf die Möglichkeiten den Code zu verbessern und führe sie durch (DRY, KISS usw.)
4. Repeat!