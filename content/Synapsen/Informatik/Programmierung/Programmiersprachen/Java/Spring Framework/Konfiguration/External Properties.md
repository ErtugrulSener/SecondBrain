## Environment (Bean) repräsentiert alle geladenen Properties zum Runtime
Reihenfolge:
- JVM System Properties - System.getProperty()
- System Environment Variables - System.getenv()
- Java Properties Files

*Wird dann in Methoden / Klassen / Konstruktoren injeziert, wenn gebraucht!*

## @PropertySource - Externe Datei laden
```Java
@Configuration
@PropertySource("classpath:/com/organization/config/app.properties")
@PropertySource("file:config/local.properties")
// http: wäre hier auch möglich!
public class ApplicationConfig {
}
```

## @Value - Bestimmte Properties laden