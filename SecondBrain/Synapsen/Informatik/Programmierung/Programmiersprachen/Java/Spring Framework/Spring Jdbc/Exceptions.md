- JdbcTemplate kümmert sich um die Exceptions!

## DataAccessException
- Spring packt die *SQLException* in eine *DataAccessException* (versteckt den Vendor dahinter, also JPA, Hibernate, JDBC usw.)
- Ist eher eine Sub-Hierarchie von Exceptions, keine "Highlander"-Lösung

![[error-code-mapping-for-exceptions.png]]

## Exception Hierarchie
![[exception-hierarchy.png]]