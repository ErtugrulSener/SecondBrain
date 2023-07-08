- Annotationen die andere [[Annotationen]] (meist von Spring selbst) darstellen
- Dazu noch weitere Konfigurationen.

```Java
@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.TYPE)
@Service
@Transaction(timeout=60)
public @interface MyTransactionalService {

}
```