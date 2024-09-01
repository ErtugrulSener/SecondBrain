- Falls unsere Klasse es erfordert (@Transactional, Security Config usw.) erstellt Spring einen Proxy und Autowired diesen, statt direkt die Klasse selbst
- Falls nicht, wird die Klasse selbst aufgerufen

## JDK Proxy vs. CGLib Proxy
- Proxys werden durch den [[1-Initialisierung#b) Beans und Abhängigkeiten zwischen ihnen erstellen]] Schritt, den *BeanPostProcessor* eingebunden
- Dieser nimmt dann das Bean entgegen und wrappt es um Proxy, das ist dann der Rückgabewert

![[proxying.png]]

## Unterschiede zwischen den zwei Proxyarten
![[cglib-vs-jdk-proxy.png]]

## Hinweise
- Spring Boot nutzt immer CGLib
- Spring entscheidet folgendermaßen:
	- Wenn die Komponente ein Interface implementiert, nutzt sie den JDK Proxy (Austausch der Komponente über Interface)
	- Wenn sie keins implementiert, nimmt sie CGLib Proxy (Subclassing)

- CGLib Proxy funktioniert nur bei nicht finalen Klassen und Methoden!