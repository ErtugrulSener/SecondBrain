- gehören zur JSR-250 Spezifikation, sind keine Spring Annotationen (gibt es auch in Java EE)
- Methoden, die keine Argumente akzeptieren und *void* zurückgeben:

z.B:
```Java
@PostConstruct
void myMethod() {

}
```

## @PostConstruct
- Wird ausgeführt nachdem alle Dependencies injected wurden

## @PreDestroy
- Wird ausgeführt wenn die Bean Instanzen zerstört werden

![[pre-destroy.png]]

- Alternative über initMethod und destroyMethod in @Bean

![[pre-destroy-2.png]]