# Neues zum buildSrc Projekt
## Gradle führt Tests in buildSrc nicht mehr immer automatisch mit aus
Mit Gradle 8 wurde es eingeführt, dass die buildSrc - also das lokale Projekt für Plugins, nicht mehr die Tests laufen lässt. Es baut nur noch eine Jar.

Dies kann gesehen werden mit:

```shell
gradle8 assemble --console verbose
```

Wenn man die Tests möchte, muss man das explizit machen mit:

```shell
gradle8 buildSrc:test --console verbose
```

## Init Skripte werden nun auch für buildSrc Projekte ausgeführt
Dies war mit Gradle Versionen < 8 noch nicht der Fall. Eine "allgemeine Init Methode für alle Projekte" war also nicht möglich.

```shell
gradle8 assemble -I init.gradle
```

Output wird sowas wie:

```
* Configure root project 'demo' from init script
* Configure project ':buildSrc' from init script
```

## buildSrc kann nun auch includeBuild haben (z.B: um ein Plugin für alle Projekte zu laden mit Vorkonfigurationen)
```Gradle
pluginManagement {
	includeBuild("../settingsPlugin")
}

plugins {
	id("test.plugin")
}
```

# Parallele Builds
## Konfigurationscache Miss führt nun auch zu parallelen Tasks
Dies war vorher nicht der Fall. Der "--parallel" Parameter ist hierfür nicht relevant.

# Cache-Cleanup Konfigurationsmöglichkeit
## Zeiten selbst festlegen je Cache
Vor Gradle 8 hatte jeder Cache in Gradle eine Laufzeit von z.B: 7 Tagen. Nun kann man das spezifizieren:

```Gradle
beforeSettings { settings ->
	settings.caches {
		releasedWrappers.removeUnusedEntriesAfterDays = 45
		snapshotWrappers.removeUnusedEntriesAfterDays = 7
		downloadedResources.removeUnusedEntriesAfterDays = 45
		createdResources.removeUnusedEntriesAfterDays = 14
	}
}
```

Dieses Skript liegt z.B: unter *~./.gradle/init.d/cache-settings.gradle*

## Cache Cleanup über DSL deaktivieren
Wir können diesen "Cache Cleanup Prozess" auch deaktivieren (Früher nur über gradle.properties möglich)

```Gradle
beforeSettings { settings ->
	settings.caches {
		cleanup = Cleanup.DISABLED
	}
}
```