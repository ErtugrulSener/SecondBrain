# Warum sollte man es nutzen?
Die settings.gradle Konfigurationen werden für alle Subprojekte übernommen und geteilt, gemeinsame Eigenschaften sind hier zu sammeln um Codedopplungen zu vermeiden.

# settings.gradle / settings.gradle.kts
Es gibt zwei Möglichkeiten eine Gradle Settings zu schreiben, entweder mit der Groovy DSL oder Kotlin DSL.

# Wichtige Parameter
## rootProject.name
Der Name des Projektes (Wichtig für erzeugte Artefakte, default: Name des Ordners, in der die settings Datei liegt)

---

## plugins
```Kotlin
plugins {
	id("plugin-abc")
}
```
Mit dem plugins Parameter kann man Konfigurationen für alle Subprojekte teilen.

---

## pluginManagement
```Kotlin
pluginManagement {
	repositories {
		gradlePluginPortal()
		google()
	}
	includeBuild("../my-build-logic")
}
```

Mit diesem Parameter gibt man die Plugin Repositories für Gradle Plugins an.

---

## dependencyResolutionManagement
```Kotlin
dependencyResolutionManagement {
	repositories {
		mavenCentral()
	}
	includeBuild("../my-other-project")
}
```

Mit diesem Parameter gibt man die Repositories an, die man für alle Unterprojekte beziehen / nutzen möchte.

---

## include
```Kotlin
include("sub-project-1")
include("sub-project-2")
```

Mit dem Include Parameter definieren wir die Subprojekte.