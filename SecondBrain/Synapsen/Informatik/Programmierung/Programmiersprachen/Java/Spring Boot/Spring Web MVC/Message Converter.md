- Nehmen einem die Konvertierung zu JSON (zum Beispiel, XML geht auch) ab
- Annotation dazu ist [[Mapping#@ResponseBody]]

## Möglichkeiten
- JAXP Source, JAXB2 mapped ibject, Jackson-Dataformat-XML
- GSON, Jackson JSON
- Feed data wie Atom/RSS
- Google Protocol buffers
- Form-based-data
- byte[], String, BufferedImage

## Auswahl des Converters
- Geht nach Mime Type der Resource im *Accept* Header, zum Beispiel:

```
GET /store/orders/123
Host: shop.spring.io
Accept: application/xml
```

## ResponseEntity
- Falls man keine automatische Responsegenerierung über Message Converter möchte, kann man dies mit einer ResponseEntity steuern

```Java
// ResponseEntity supports a "fluent" API for creating a
// response. Used to initialize the HttpServletResponse.
ResponseEntity<String> response =
	ResponseEntity.ok()
					.contentType(MediaType. TEXT_PLAIN)
					.body("Hello Spring");
```