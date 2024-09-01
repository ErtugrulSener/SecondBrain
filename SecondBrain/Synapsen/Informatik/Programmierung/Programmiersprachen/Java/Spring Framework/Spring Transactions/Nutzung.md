- *@EnableTransactionManagement* auf einer @Configuration Bean
- PlatformTransactionManager Bean erstellen
- *@Transactional* Annotation nutzen

## Implementationen
- DataSourceTransactionManager (default in Spring Boot)
- JmsTransactionManager
- JpaTransactionManager
- JtaTransactionManager
- WebLogicJtaTransactionManager
- WebSphereUowTransactionManager
- usw..

## PlattformTransactionManager Bean
```Java
@Bean
public PlattformTransactionManager transactionManager(DataSource dataSource) {
	return new DataSourceTransactionManager(dataSource);
}
```

## @Transactional
```Java
@Transactional
public xy abc() {

}
```
- Transaktion ist an den aktuellen Thread gebunden (also gültig innerhalb des Threads!)
- Man kann auf die Connection auch zugreifen über: `DataSourceUtils.getConnection(dataSource);`

## @Transaction(timeout=xy)
- Timeout für die Transaktion
- Annotation auf Methode hat Vorrang über Annotation auf der Klasse

## AOP
![[transactional-aop-example.png]]