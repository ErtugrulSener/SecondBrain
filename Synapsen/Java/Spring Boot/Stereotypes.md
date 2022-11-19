# Spring Annotationen
- Dienen dem Springframework als Metadaten über ein Programm
- Haben keinen direkten Einfluss auf die Operationen des kompilierten Programms, eher indirekt durch Dependency Injection oder automatische Konfigurationen

# Stereotypes
Es gibt drei Hauptannotationen im Spring-Framework:
- @Service
- @Repository
- @Controller

# Architektur

![[Stereotype_annotations.png]]

Package für alle hier erwähnten Annotationen:
org.springframework.stereotype

```ad-note
Wir markieren diese Klassen damit als "spring managed component".
Deswegen der Name @Component.
```

# Gemeinsamkeiten
- Alle sind Ableitungen ("Subklassen") von @Component
- Alle Annotationen registrieren die Klasse als [[Spring Bean]]
- Alle Spring Beans werden dann im Application Context verwaltet bzw. können von da referenziert werden

# Unterschiede
## 1) @Service
Eine mit @Service annotierte Klasse enthält die Business Logik eines Programms. Auch Utility-Klassen werden manchmal mit @Service annotiert werden. Sonst hat es keine weitere Funktion, es handelt sich um ein Marker-Interface.

## 2) @Repository
Mit @Repository annotierte Klassen benutzen CRUD Operationen, die mit der Datenbank "sprechen".

## 3) @Controller
Die Annotation @Controller ist ein Indikator für eine Klasse die die Front Controller (Schnittstellen) anbietet, User Requests entgegennimmt, auflöst und Responses zurückgibt. Meist wird diese Annotation in Rest Web Services genutzt.