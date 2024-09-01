Durch das Nutzen von [[Stereotypes]] können wir Annotationen für die Konfiguration unserer Anwendung nutzen.

## @ComponentScan
Damit das funktioniert, müssen wir neben einer `@Configuration` Annotation auch das `@ComponentScan` angeben, um unserer Anwendung zu sagen, wo er die Komponenten (`@Service`, `@Repository`, `@Configuration`) finden kann.

## @Autowired
- Hat ein Attribut `required` was man auf `false` setzt, falls man diese Dependency nicht für das Startup der Anwendung braucht
- Alternative: `Optional<AccountService>`, dann weiß Spring auch, dass der Bean an dieser Stelle nicht required ist und die Anwendung stürzt nicht ab

## 3 Arten von Dependency Injections
- Konstruktor (Empfohlen, für Testbarkeit später)
- Method (Empfohlen, falls sich die Dependency in Runtime ändern darf)
- Field