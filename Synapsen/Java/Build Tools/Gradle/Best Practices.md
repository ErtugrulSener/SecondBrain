1) Immer den Gradle Wrapper nutzen
2) Das .gradle - Verzeichnis gehört nicht in die VCS
3) Führe gradle.init in einem eigenen Ordner aus
4) Wenn du die Groovy DSL für deine Gradle Builds nutzt, solltest du in den Gradle Wrapper Konfigurationen die Gradle distribution auf "all" stellen
5) Es ist empfohlen, immer mindestens ein Subprojekt zu haben. Standartmäßig nennt Gradle das "app"
6) Gradle wird in der Konfigurationsphase alle [[build.gradle]] Dateien parsen, daher bietet es sich an immer das Projekt mitzugeben wenn man einen Task ausführt: "./gradlew :app:run"
7) Man sollte den "mainClassName" beim Plugin "application" auch als Manifest Attribut setzen:

```Groovy
jar {  
    manifest {  
        attributes(  
                'Main-Class': "$mainClassName"  
        )  
    }  
}
```

8) Manchmal führen einfach mehrere Wege nach Rom, wichtig ist, das man konsistent ist mit den Wegen die man in den build.gradle Skripten nutzen will. Beispiel:

## Das Plugin 'application' anwenden

Für die Groovy DSL z.B:

```Groovy
plugins {
	id 'application'
	id "application"
	id('application')
	id("application")
	
	apply 'application'
	apply "application"
	apply('application')
	apply("application")
}
```

9) Für die Entwicklung empfehle ich den Flag "org.gradle.console" auf "verbose" zu setzen in der gradle.properties für mehr Konsolenoutput.