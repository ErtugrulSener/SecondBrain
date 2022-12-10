# Warum sollte man es nutzen?
Die build.gradle Konfigurationen werden jeweils pro Subprojekt erstellt und beinhalten spezifische Informationen für ein Projekt.

# Aufbau einer build.gradle Datei
- Plugins (Zusätzliche Buildfunktionalitäten)
- Build Metadaten (Informationen zu meinem Build)
- Repositories (Wo sind meine Dependencies?)
- Dependencies (Requirements um meinen Code zu bauen)

# Welche 3 Dinge gehören in die build.gradle?
- Plugins
- Extensions (Einstellungen zur Kompilierung z.B: java.toolchain usw.)
- Dependencies

```ad-warning
Der Rest gehört in Plugins, um die build.gradle Datei nicht unübersichtlich lang zu machen!
```

# build.gradle / build.gradle.kts
Es gibt zwei Möglichkeiten eine Gradle Builddatei zu schreiben, entweder mit der Groovy DSL oder Kotlin DSL.

# Wichtige Parameter
## plugins
```Kotlin
plugins {
	id("java-library")
}
```
Mit dem plugins Parameter kann man Konfigurationen für ein Subprojekt laden, damit erhält man zum Beispiel Tasks und andere (von Gradle definierte) Einstellungen werden für einen für dieses Subprojekt eingestellt.

---

## toolchain
```Kotlin
java {
	toolchain.languageVersion.set(JavaLanguageVersion.of(17))
}
```
So setzt man die Java Version für das Java Toolchain, um zu spezifizieren welche Java Version wir als Output vom Compiler erwarten. Dementsprechend muss dann auch eine JDK konfiguriert sein, die diese erzeugen kann. (Gleich oder höher der Version 17)

---

## dependencies
```Kotlin
dependencies {
	implementation(project(":sub-project-2"))
	implementation("org.apache.commons:commons-lang3:3.9")
}
```
Mit den Dependencies spezifizieren wir, welche Abhängigkeiten wir besitzen. Auch Abhängigkeiten zu anderen Projekten sind möglich.