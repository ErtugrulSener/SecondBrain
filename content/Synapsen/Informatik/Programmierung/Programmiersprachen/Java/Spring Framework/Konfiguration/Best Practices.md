## Autowiring mit mehreren Konstruktoren
- Wenn eine Klasse *nur den Default Konstruktor* hat, kann man die @Autowired Annotation weglassen
- Wenn eine Klasse *nur den Non-Default Konstruktor* hat, gilt das Selbe
- Wenn eine Klasse *mehr als einen* Konstruktor hat, dann ruft String den No-Arg-Konstruktor auf (außer man überschreibt es mit @Autowired)

## Component scanning
So genau wie möglich, also zum Beispiel:

```Java
@ComponentScan({"com.app.repository", "com.app.service", "com.app.controller"})
```

## Annotation (Stereotypes) vs. Java Configuration (Beans)
- Java Configuration mit [[Beans]] vor allem dann, wenn man die Klasse nicht besitzt, die man konfigurieren möchte.
- Ergo man mus gezwungen Beans zu nutzen, das gilt bei vielen Frameworks für Web MVC