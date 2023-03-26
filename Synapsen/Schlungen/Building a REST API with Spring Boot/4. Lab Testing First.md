## @JsonTest
Falls man die simpelsten Jackson Funktionalitäten (serialisieren und deserialisieren von JSON und Java-Beans) in Tests benötigt, nutzt man die @JsonTest Marker-Annotation.

Anschließend kann man noch die Klasse *JacksonTester* nutzen, die automatisch injiziert wird in Runtime.

```Java
@JsonTest
public class CashCardJsonTest {

    @Autowired
    private JacksonTester<CashCard> json;

	... Your tests here
```