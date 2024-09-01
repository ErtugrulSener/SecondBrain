- eine Art Pipeline, die Events speichert
- Hinzufügen von weiteren Events, das Reproduzieren von Events und der parallele Zugriff auf Events muss sehr schnell gehen
	- DBMS würde funktionieren, ist aber womöglich nicht das richtige Tool dafür
	- Mögliche Implementationen dafür:
		- EventStore - Greg Young
		- AxonDB - AxonIQ

*Beispiel Szenario:*
- Kunde A legt einen Apfel in den Warenkorb
- Kunde A legt einen Stift in den Warenkorb
- Kunde A entfernt den Apfel
- Kunde A führt Kauf durch
- Kunde A verlässt die Seite

## Okay... aber warum?
- Diese Events können nun analysiert werden, aus Business-Sicht ist es im Beispielszenario zum Beispiel interessant zu wissen, warum Kunde A den Apfel entfernt hat
- Hat der Prozess ihm zu lange gedauert?