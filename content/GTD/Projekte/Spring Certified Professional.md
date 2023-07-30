## Spring Academy Tutorials
Learning Path: https://spring.academy/paths/spring-certified-professional-2023
Current: https://spring.academy/courses/spring-framework-essentials/lessons/spring-essentials-java-config-quickstart

- [x] 1 - Build a REST API with Spring Boot

- [x] 2 - Spring Framework Essentials
	- [x] Modul 1: Spring Essentials Overview
	- [x] Modul 2: Java Configuration
	- [x] Modul 3: More on Java Configuration
	- [x] Modul 4: Component Scanning
	- [x] Modul 5: Inside the Spring Container
	- [x] Modul 6: Introduction to Aspect Oriented Programming
		- [x] Part 1
		- [x] Part 2
		- [x] Übung
	- [x] Modul 7: Testing Spring Applications
	- [x] Modul 8: JDBC Simplification with Jdbc Template
	- [x] Modul 9: Transaction Management with Spring

- [x] 3 - Spring Boot
	- [x] Modul 1: Spring Boot Feature Introduction
	- [x] Modul 2: Spring Boot - A Closer Look
	- [x] Modul 3: Spring Boot - Spring Data JPA
	- [x] Modul 4: Web Application with Spring Boot
	- [x] Modul 5: RESTful Application with Spring Boot
	- [x] Modul 6: Spring Boot Testing
	- [x] Modul 7: Securing REST Application with Spring Security
	- [x] Modul 8: Actuator

## Kurs zum Spring Professional Certification Exam auf Udemy machen
Link: https://www.udemy.com/course/spring-certified-tutorial/
Module: 8

### Modul 1
#### Was ist Dependency Injection und was sind die Vorteile?
- Eine Technik, bei der die Abhängigkeiten für ein Objekt durch extern erstellt werden und nicht mehr von ihr selbst.
- Das Objekt spezifiziert seine Dependencies und ein Externes Objekt oder ein Framework gibt die konkreten Implementationen an.
<br>
- 3 mögliche Wege:
	- Constructor Injection
	- Setter Injection
	- Interface Injection

#### Was ist ein Pattern? Was ist ein Anti-Pattern? Ist Dependency Injection ein Pattern?
- Ein Pattern ist eine wiederverwendbare Lösung (ein Template) welches angewandt wird, um sich die Art der Lösungen nicht neu ausdenken zu müssen
- Es hilft Zeit zu sparen und hilft der Produktivität des Entwicklers
<br>
- *Beispiele für Patterns*
	- Factory Method
	- Template Method
	- Observer
	- Builder
	- Command
	- Facade
	- Visitor
<br>
- *Beispiele für Anti-Patterns:*
	- God Object
	- Sequential Coupling
	- Cyclic Dependency
	- Constant Interface
<br>
- Dependency Injection ist ein Pattern. Es löst das Problem, Abhängigkeiten zu erstellen
- Beispiel: Command-Pattern hat zwei Methoden *canExecute* und *execute*

#### Was ist ein Interface und was sind die Vorteile in der Nutzung davon in Java? Warum sind sie für Java Beans empfohlen?
Ein Interface definiert die Schnittstelle (die öffentlichen Methoden) einer Klasse, der Nutzer dieser Klasse (intern oder extern) kann sich auf die im Interface deklarierten Methoden verlassen.

Außerdem können sich einige Klassen das Interface teilen, wobei ihre Implementierung sich unterscheidet. Genau diese Implementierung kann dann zur Laufzeit ausgetauscht werden, auch Mocking wird durch Interfaces (bzw. die interfacebasierte Programmierung) ermöglicht für Tests.

Außerdem hilft es dem "Loose Coupling", also der losen Kupplung zwischen Klassen.

- Für Spring:
	- Implementation Hiding
	- Beans zur Laufzeit austauschen
	- Dynamic JDK Proxy (Achtung, in Spring Boot wird immer CG Lib verwendet)