## Klasse als API registrieren
```Java
@GraphQLApi
@Component
public class PrayerTimesAPI {  
	[...]
}
```

```ad-note
Wir fügen außerdem die Annotation @Component hinzu, damit wir eine Spring managed Bean haben, die wir über Autowiring später wiederverwenden können!
```

## Query erstellen
```Java
public class Demo {
	@GraphQLQuery
	public DTO query() {
		return [...];
	}
}
```

## Mutation erstellen
```Java
public class Demo {
	@GraphQLMutation
	public DTO mutate() {
		return [...];
	}
}
```

## Feldern Namen und Beschreibungen geben
```Java
public class PrayerTimesAPI {  
    @GraphQLQuery  
    public PrayerTimeDTO findPrayerTimesForCity(@GraphQLArgument(name = "city") String city) {  
        return new PrayerTimeDTO();  
    }  
}
```

## GraphQL Schema auf Dateisystem erstellen
```Java
	@Test
	void generateGraphQLSchema() throws IOException {
		GraphQLSchema schema = new GraphQLSchemaGenerator().withOperationsFromSingleton(personAPI, PersonAPI.class)
				.withOperationsFromSingleton(vernehmungAPI, VernehmungAPI.class)
				.withOperationsFromSingleton(grunddatenVorgangAPI, GrunddatenVorgangAPI.class)
				.withOperationsFromSingleton(beschuldigtenvernehmungAPI, BeschuldigtenvernehmungAPI.class)
				.withOperationsFromSingleton(vorgangAPI, VorgangAPI.class)
				.generate();

		String str = new SchemaPrinter().print(schema);
		File newFile = new File("schema.graphqls");
		var fileWriter = new FileWriter(newFile);
		fileWriter.write(str);
		fileWriter.close();
	}
```