Wenn man Spring Data JPA (starter) im Classpath hat, werden folgende Dinge automatisch konfiguriert:
- Eine *DataSource*
- Ein *EntityManagerFactoryBean*
- Ein *JpaTransactionManager*

## @EntityScan
Mit dieser Annotation kann man angeben, wo die JPA Entities (Modelle) liegen
Dies ist nur nötig, wenn sie nicht im selben oder in einem Unterverzeichnis (relativ zur Main-Applikationsklasse) sind.