Spring Boot erstellt eine *PropertySource* Bean, wenn man die *application.properties* in bestimmten Pfaden hat. (z.B: im Classpath Root also src/main/resources oer auch in einem /config Ordner)

## @PropertySource
- Wenn man selbst Properties laden möchte und sie (aus welchen Gründen auch immer) nicht in die application.properties tun möchte, kann man die @PropertySource Annotation verwenden

```Java
@PropertySourc("my/dir/to/my.properties")
public class myProperties() {

}
```

## @ConfigurationProperties
- Klasse erstellen, die alle Properties hält
- Wie schalte ich dieses Feature an?
	- `@EnableConfigurationProperties(MySettings.class)`
	- `@ConfigurationPropertiesScan`
	- `@Component` (bevorzugt, weil die Klasse dann eine Bean ist und zur Laufzeit verwendet werden kann)

## Relaxed Binding Feature
![[relaxed-binding.png]]

## Profile-specific-Properties
- Folgen dem Schema:
`application-<profile>.properties`

z.B:
- application-dev.properties

## YML Alternative
- Man kann die Properties auch als *.yml* nutzen
- Vorteile:
	- Nutzen von Gruppen (--- steht für eine logische Gruppe)

```YAML
spring
  datasource: xy

---
spring:
  profiles: local
  datasource: abc

---
spring:
  profiles: remote
  datasource: abc123
```