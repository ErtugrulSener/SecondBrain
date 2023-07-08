 ## Konfiguration über Beans
- Beans befinden sich dann im Application Context
- Abhängigkeiten zwischen Beans können gesetzt werden

## Abhängigkeiten herstellen
- können über Argumente an Methoden / Konstruktoren hergestellt werden
- können explizit über Autowiring (Feld in der Klasse) hergestellt werden

## Abhängigkeiten untereinander herstellen
- Spring kümmert sich um die Reihenfolge, in der die Abhängigkeiten hergestellt werden müssen (Abhängigkeiten zwischen Beans)

## @Configuration + @Bean vs. @Component
Man kann Abhängigkeiten auf diesen zwei angegebenen Wegen festlegen.
Siehe auch [[Spring Bean]] und [[Stereotypes]]

## Loose Coupling
- Man sollte Interfaces anstelle von Klassen nutzen, muss es aber nicht