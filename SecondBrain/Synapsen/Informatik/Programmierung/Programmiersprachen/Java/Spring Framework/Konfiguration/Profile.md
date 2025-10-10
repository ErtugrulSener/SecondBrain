- Kann eine Umgebung darstellen, z.B: dev, test, production
- Oder eine Implementierung: jdbc, jpa
- Oder eine Deployment Plattform: on-premise, cloud

## Funktionsweise
- [[Beans]] lassen sich damit inkludieren oder exkludieren
- Not Operator (!) ist möglich

## Aktivieren des Profiles
- Über System Property: `-Dspring.profiles.active=embedded,java`
- Über System Property (Runtime, bevor die Applikation startet):
```java
System.setProperty("spring.profiles.active", "embedded,jpa");
SpringApplication.run(AppConfig.class);
```
- In Tests: @ActiveProfiles