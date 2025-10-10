# Dependencies für einen Task spezifizieren
Ein Task kann von anderen Tasks abhängen (wie im Gradle Task Graph auch zu sehen).

## dependsOn
Die erste Möglichkleit hierfür ist der dependsOn Befehl im Task selbst.

```Groovy
task beforeTest {
	dependsOn "test"

	println 'Run before test'
}
```

## from
Statt über dependsOn explizit den Task davor anzugeben, arbeitet man damit zu sagen "Mein Input ist der Output X", damit kann Gradle dann seine üblichen Caching Geschichten machen.

```Groovy
task beforeTest {
	println 'Run before test'
	
	from(tasks.test) { include("**/*.xml") }
}
```

Man nennt dies auch eine "infered task dependency"

## inputs
Eine Alternative Schreibweise für "from" ist es, die Inputs direkt zu beschreiben. Vllt. sogar etwas einfacher.

```Groovy
task beforeTest {
	inputs.files(tasks.test)
	println 'Run before test'
}
```

## finalizedBy
Der Task zuvor, könnte auch den nächsten Task aufrufen.

```Groovy
task afterTest {
	println 'Run before test'
}

test {
	finalizedBy(tasks.named("afterTest"))
}
```
