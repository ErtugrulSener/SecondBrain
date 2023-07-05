- Managed die [[Beans]]
- Kann in jeder Umgebung erstellt werden (Standalone Application, Web application, JUnit test)

## Beispielcode für JUnitTest
```Java
public class TransferServiceTests {
	private TransferService service;

	@BeforeEach
	public void setUp() {
		ApplicationContext context = SpringApplication.run(ApplicationConfig.class);
		service = context.getBean(TransferService.class);
	}
}
```