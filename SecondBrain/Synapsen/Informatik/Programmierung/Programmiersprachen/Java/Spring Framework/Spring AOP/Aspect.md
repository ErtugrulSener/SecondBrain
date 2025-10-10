```Java
@Aspect
@Component
public class PropertyChangeTracker {
	private Logger logger = Logger.getLogger(getClass());

	@Before("execution(void set*(**))")
	public void trackChange() {
		logger.info("Property about to change...")
	}
}
```

Für mehre Informationen siehe [[Synapsen/Informatik/Programmierung/AOP/Konzepte/Aspect|Aspect]]