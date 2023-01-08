# Arten von Dependencies
- Module (dependencies in build.gradle)
- Andere Gradle Projekte
- Datei (nicht empfohlen)

# Transitive Dependencies
Das sind Dependencies von Dependencies. Folgender Befehl hilft bei der Analyse:

```Bash
gradle dependencies
```

Gradle holt sich diese automatisch.

# api vs. implementation
Der Unterschied zwischen api und implementation als Dependency Configuration ist dieser Unterschied:
- api wird genutzt, wenn diese Dependency sowohl zur Kompilierung als auch für Runtime gebraucht wird
- implementation wird genutzt, wenn diese Dependency nur zur Runtime gebraucht wird

# Versioning
- 2.3 oder später
```Groovy
implementation("org.company:some-lib:2.3")
```

- Strikt 2.3
```Groovy
implementation("org.company:some-lib:2.3!!")
```

- Latest 2.+Version
```Groovy
implementation("org.company:some-lib:2.+")
```

- SNAPSHOT of 2.7
```Groovy
implementation("org.company:some-lib:2.7-SNAPSHOT")
```

# Wie setzt sich ein Module zusammen?
Group + Library Name

Also:

com.google.guava + guava

# Modules
Gradle nennt Artefakte einfach "Modules", weil sie sich mit der Zeit weiterentwickeln und ihre Versionsnummer inkrementiert wird.

Sie bestehen aus folgenden drei Bestandteilen:
- Dependency Konfiguration (Scope)
- Modul
- Modul Version

![[module-parts.png]]

```Groovy
dependencies {
	implementation "com.google.guava:guava:30.1.1-jre"
}
```

# Repositories
Repositories sind ein Host für ein Set von Modulen
- Jedes Modul kann dabei mehrere Releases haben
- Wo finde ich meine Module?

```Groovy
repositories {
	mavenCentral()
}
```