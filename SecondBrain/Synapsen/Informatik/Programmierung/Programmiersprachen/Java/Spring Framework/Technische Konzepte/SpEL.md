- Spring Expression Language

## Historie
- Ursprung im Spring WebFlow Projekt
- Basiert auf *Unified Expression Language*, was in *JSP* und *JSF* genutzt wurde
- Wird auch in anderen Spring-basierenden-Frameworks (Spring Security zum Beispiel) benutzt

## System Property mit @Value zuweisen
```Java
@Configuration
class TaxConfig {
	@Value("#{systemProperties['user.region']}") String region;
}
```

## Ein Bean referenzieren
```Java
@Configuration
class StrategyConfig {
	@Bean public StrategyBean strategyBean() {
		return new StrategyBean();
	}
}

@Configuration
@Import(StrategyConfig.class)
class AnotherConfig {
	// Achtung, das ruft den Getter auf!
	@Value("#{strategyBean.keyGenerator}") KeyGenerator keygen;
}
```

## Falle: Variablen in SpEL
```ad-note
Variablen in SpEL sind grundsätzlich zunächst vom Typ 'String' und MÜSSEN explizit gecastet werden (mit new Integer(...) z.B) wenn man Berechnungen an dieser Stelle machen möchte!
```

```Java
@Value("#{new Integer(environment['today.day']) * 2}") Integer day;
```

## Default Werte
```java
@Value("${daily.limit : 100000}") int max;

// ODER in SpEL

@Value("#{environment['daily.limit'] ?: 100000}") int max;
```