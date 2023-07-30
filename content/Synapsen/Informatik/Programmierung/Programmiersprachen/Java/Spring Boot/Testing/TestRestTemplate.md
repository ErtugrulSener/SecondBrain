Nutzt man, damit man keine absoluten Pfade angeben muss wie bei *RestTemplate*. Der Pfad zum Embedded Tomcat wird automatisch anvisiert / konfiguriert.

- Ignoriert Cookies
- Ignoriert Weiterleitungen

```Java
@Autowired
private TestRestTemplate restTemplate;
```