## @Import
- über die @Import Annotation mehrere Konfigurationen in einer großen Konfiguration zusammenfassen, aber in eigene Klassen trennen / auslagern
- *Seperation of Concerns*
```Java
@Configuration
@Import({ApplicationConfig.class, WebConfig.class})
public class InfrastructureConfig {
	...
}
```

## @Autoried
- In Konstruktur
- In Feld
- In Setter-Methode

## Good Practice:
- Infrastruktur und Application Configuration trennen
	- Also sowas wie ein Bean für Postgres trennen von einem Bean von der Applikation
	- Eine Highlander Klasse "ApplicationConfig" reicht dann nicht!#

- "Tramp Data" verhindern, Abhängigkeiten wirklich nur bei dem Bean wo es gebraucht wird. Beispiel dafür:
- 
![[tramp-data.png]]