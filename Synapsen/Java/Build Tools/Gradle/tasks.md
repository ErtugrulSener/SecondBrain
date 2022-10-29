# Welche Tasks bringt Gradle standartmäßig mit und wie sehe ich sie?

Um alle Tasks von Gradle zu sehen hilft folgender Befehl:

```bash
gradle tasks
```

Unter anderem wird man dort folgende Dinge finden:

---

## buildEnvironment
Zeigt alle Buildscript-Dependencies im gradle.build Skript des aktuellen Projektes (Bzw. Subprojektes) in folgender Form:

```ad-note
collapse: true
title: Output

------------------------------------------------------------
Project ':app'
------------------------------------------------------------

classpath
\--- project :LearningGradlePlugins:java-plugins
```

Diese Dependencies werden nur von dieser [[build.gradle]] Datei verwendet und nicht vom Projekt selbst, denn dafür gibt es...

---

## dependencies
Hier sieht man alle Dependencies des Projektes, die Buildscript-Dependencies sind natürlich nicht in der Liste.

```ad-note
collapse: true
title: Output

------------------------------------------------------------
Project ':app'
------------------------------------------------------------

annotationProcessor - Annotation processors and their dependencies for source set 'main'.
No dependencies

api - API dependencies for source set 'main'. (n)
No dependencies

apiElements - API elements for main. (n)
No dependencies

archives - Configuration for archive artifacts. (n)
No dependencies

compileClasspath - Compile classpath for source set 'main'.
\--- org.apache.commons:commons-lang3:3.12.0

compileOnly - Compile only dependencies for source set 'main'. (n)
No dependencies

compileOnlyApi - Compile only API dependencies for source set 'main'. (n)
No dependencies

default - Configuration for default artifacts. (n)
No dependencies

implementation - Implementation only dependencies for source set 'main'. (n)
\--- org.apache.commons:commons-lang3:3.12.0 (n)

mainSourceElements - List of source directories contained in the Main SourceSet. (n)
No dependencies

runtimeClasspath - Runtime classpath of source set 'main'.
\--- org.apache.commons:commons-lang3:3.12.0

runtimeElements - Elements of runtime for main. (n)
No dependencies

runtimeOnly - Runtime only dependencies for source set 'main'. (n)
No dependencies

testAnnotationProcessor - Annotation processors and their dependencies for source set 'test'.
No dependencies

testCompileClasspath - Compile classpath for source set 'test'.
+--- org.apache.commons:commons-lang3:3.12.0
\--- org.junit.jupiter:junit-jupiter-api:5.8.1
     +--- org.junit:junit-bom:5.8.1
     |    +--- org.junit.jupiter:junit-jupiter-api:5.8.1 (c)
     |    \--- org.junit.platform:junit-platform-commons:1.8.1 (c)
     +--- org.opentest4j:opentest4j:1.2.0
     +--- org.junit.platform:junit-platform-commons:1.8.1
     |    +--- org.junit:junit-bom:5.8.1 (*)
     |    \--- org.apiguardian:apiguardian-api:1.1.2
     \--- org.apiguardian:apiguardian-api:1.1.2

testCompileOnly - Compile only dependencies for source set 'test'. (n)
No dependencies

testImplementation - Implementation only dependencies for source set 'test'. (n)
\--- org.junit.jupiter:junit-jupiter-api:5.8.1 (n)

testResultsElementsForTest - Directory containing binary results of running tests for the test Test Suite's test target. (n)
No dependencies

testRuntimeClasspath - Runtime classpath of source set 'test'.
+--- org.apache.commons:commons-lang3:3.12.0
+--- org.junit.jupiter:junit-jupiter-api:5.8.1
|    +--- org.junit:junit-bom:5.8.1
|    |    +--- org.junit.jupiter:junit-jupiter-api:5.8.1 (c)
|    |    +--- org.junit.jupiter:junit-jupiter-engine:5.8.1 (c)
|    |    +--- org.junit.platform:junit-platform-commons:1.8.1 (c)
|    |    \--- org.junit.platform:junit-platform-engine:1.8.1 (c)
|    +--- org.opentest4j:opentest4j:1.2.0
|    \--- org.junit.platform:junit-platform-commons:1.8.1
|         \--- org.junit:junit-bom:5.8.1 (*)
\--- org.junit.jupiter:junit-jupiter-engine:5.8.1
     +--- org.junit:junit-bom:5.8.1 (*)
     +--- org.junit.platform:junit-platform-engine:1.8.1
     |    +--- org.junit:junit-bom:5.8.1 (*)
     |    +--- org.opentest4j:opentest4j:1.2.0
     |    \--- org.junit.platform:junit-platform-commons:1.8.1 (*)
     \--- org.junit.jupiter:junit-jupiter-api:5.8.1 (*)

testRuntimeOnly - Runtime only dependencies for source set 'test'. (n)
\--- org.junit.jupiter:junit-jupiter-engine:5.8.1 (n)
```

## dependencyInsight
Gibt dir spezifische Einblicke in eine bestimmte Dependency. Der Befehl könnte zum Beispiel so aussehen:

```Bash
gradle dependencyInsight --dependency commons-lang3
```

---

##  help
Gibt eine Help-Message aus.

---

## javaToolchains
Zeigt alle gefundenen jdks, dafür wird in Standartpfaden gesucht wie *%USERPROFILE%/.jdks* usw. 

```ad-note
collapse: true
title: Output

 + OpenJDK 18.0.2+9-61
     | Location:           C:\Users\Lead\.jdks\openjdk-18.0.2
     | Language Version:   18
     | Vendor:             Oracle
     | Architecture:       amd64
     | Is JDK:             true
     | Detected by:        IntelliJ IDEA

 + Zulu JDK 18.0.2+9
     | Location:           C:\Users\Lead\.jdks\azul-18.0.2
     | Language Version:   18
     | Vendor:             Zulu
     | Architecture:       amd64
     | Is JDK:             true
     | Detected by:        IntelliJ IDEA
```