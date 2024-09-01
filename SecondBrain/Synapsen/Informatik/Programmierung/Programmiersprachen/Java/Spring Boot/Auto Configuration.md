## Abfolge
- Erst schaut Spring auf alle konfigurierten Beans im Source Code des Entwicklers
- Wenn hier was fehlt, kommt die AutoConfiguration ins Spiel
	- @AutoConfiguration
	- `spring-boot-autoconfigure/META-INF/spring/org.springframework.boot.autoconfigure.AutoConfiguration.imports`

## @EnableAutoConfiguration
## @SpringBootApplication
```Java
@SpringBootApplication
public class Application {

}
```

- Scannt den Classpath nach Klassen, die mit @Configuration annotiert sind.
- Diese Klassen haben teilweise auch *Conditions*, werden also nur bei bestimmten Zuständen geladen.
	- Beispiel:
		- Du hast Spring Startet JDBC im Classpath -> Versuche eine DataSource Bean zu erstellen -> JdbcTemplate Bean erstellen

## @ConditionalOnBean
```Java
@Bean
@ConditionalOnBean(DataSource.class)
public JdbcTemplate jdbcTemplate(DataSource dataSource) {
    return new JdbcTemplate(dataSource);
}
```
- Bean laden, falls eine andere Bean existiert

## @ConditionOnMissingBean
- Gegenteil von [[#@ConditionalOnBean]]