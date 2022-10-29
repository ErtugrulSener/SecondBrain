# Wie erstelle ich ein Gradle-Plugin?
Gar nicht! Ich erstelle ein weiteres gradle - Build, seperat von meinem aktuellen Projekt und nutze dann die

```Kotlin
includeBuild("my-build-logic")
```

Funktion im pluginManagement, siehe hier: [[settings.gradle - settings-file#pluginManagement]]

# Welche drei Arten von Gradle Plugins gibt es?
## Core Plugins
Diese werden mit Gradle ausgeliefert und können über den id-Befehl unter Plugins im [[build.gradle - build-file]] oder für alle Subprojekte in der [[settings.gradle - settings-file]]eingeführt werden. Selbiges gilt für die nächsten zwei Plugin-Arten.

```Kotlin
plugins {
	id("java-library")
}
```

## Community Plugins
Welche überlicherweise im Gradle Plugin Repository hochgeladen werden. Sie werden üblicherweise über ihre Id und eine Version deklariert.
```Kotlin
plugins {
	id("org.jetbrains.kotlin.jvm") version "1.5.21"
}
```

## Convention Plugins
Plugins, die man selbst schreibt und die nur lokal existieren.