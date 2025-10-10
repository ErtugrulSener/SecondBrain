- Besteht intern aus 2 Phasen:
	- a) Definitionen für Beans in BeanFactory (ApplicationContext) speichern
	- b) Beans erstellen und alle Abhängigkeiten zwischen ihnen über DI setzen

## Beispiel Code
```Java
ApplicationContext context = SpringApplication.run(AppConfig.class);
// Initalisierung ist hiermit beendet
```

## Schritte der Initialisierung
1) Bean Definitionen laden
2) Bean Definitions Post Process Phase
3) Abhängigkeiten zwischen Beans herstellen
4) Beans initialisieren (nacheinander)
5) Setter Injections durchführen
6) Bean Post Process Phase

## a) Bean-Definitionen laden
- nach dem Laden findet ein "Post Process Bean Definitions" Schritt statt.
- Zum Beispiel sorgt dieser bei @Value dafür, dass der der Variable von *${my.property}* mit der Konfiguration aus der *application.properties* erzeugt wird.

```ad-note
Die Klasse, in der alle Beans indexiert sind mit ihrer unique id und ihrem Typ implementiert das Interface BeanFactory.

Die Klasse, die ein Bean Post Processing vornimmt, implementiert das Interface BeanFactoryPostProcessor. Wenn man selbst einen Processor schreiben möchte, muss die Bean static markiert sein.
```

Schaubild:
![[bean-factory.png]]

## b) Beans und Abhängigkeiten zwischen ihnen erstellen
- Jede Bean geht durch eine post-processing Phase
- Nutze das *BeanPostProcessor* Interface um eine BeforeInit und AfterInit Methode für Beans zu spezifizieren

![[custom-bean-post-processor.png]]