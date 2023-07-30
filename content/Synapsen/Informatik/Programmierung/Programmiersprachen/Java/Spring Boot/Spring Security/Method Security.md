- Spring Security nutzt AOP
	- Spring eigene Annotationen oder JSR-250
- Services sollten gesichert werden

![[method-security.png]]

## @EnableMethodSecurity
- Muss an einer Konfigurationsklasse geschrieben werden, damit man die folgenden Annotationen nutzen kann

## @PreAuthorize("hasRole('ADMIN')")
## @PostAuthorize(...)
- nennt sich 'Expression-based access control'