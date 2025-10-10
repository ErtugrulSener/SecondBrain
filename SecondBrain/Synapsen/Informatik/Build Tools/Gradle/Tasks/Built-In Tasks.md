# Welche Tasks bringt Gradle standartmäßig mit und wie sehe ich sie?

Um alle Tasks von Gradle zu sehen hilft folgender Befehl:

```bash
gradle tasks
```

Unter anderem wird man dort folgende Dinge finden:

---

## init
Startet ein Prozess um ein neues Gradle Projekt zu erstellen (Ähnlich wie bei start.spring.io)

## wrapper
Generiert die Gradle Wrapper Dateien

Um die Version zu setzen, kann man entweder die gradle-wrapper.properties unter:
*./gradle/wrapper/gradle-wrapper.properties* selbst bearbeiten oder folgenden Befehl ausführen:

```Bash
gradle wrapper --gradle-version 7.5.1 --distribution-type all
```

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

---

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

---

## projects
Zeigt alle Subprojekte des Rootprojektes an.

---

## properties
Zeigt alle properties für das Rootprojekt an. Dies sind größtenteils Properties, die Gradle oder ein inkludiertes Plugin für einen gesetzt haben. Wichtige und nützliche darunter sind z.B:

| Name       | Bedeutung                                                      | Beispielwert                                              |
| ---------- | -------------------------------------------------------------- | --------------------------------------------------------- |
| buildDir   | Pfad für den 'build' Ordner, liegt neben der [[build.gradle]]. | C:\Users\Lead\Desktop\Ertu-Git\cleanprojeect\build        |
| buildFile  | Pfad zur [[build.gradle]] Datei                                | C:\Users\Lead\Desktop\Ertu-Git\cleanprojeect\build.gradle |
| projectDir | Pfad zum Rootprojekt                                           | C:\Users\Lead\Desktop\Ertu-Git\cleanprojeect              |
| name       | Name des Rootprojektes                                         | cleanproject                                              |
| group      | Spezifizierte Group für die Artefakte                          | org.mygroup                                                         |
| version    | Spezifizierte Version für die Artefakte                        | 1.0-SNAPHOT                                                          |

---

## tasks
Zeigt eine Liste mit allen vorhandenen Gradle Tasks. Untenstehend alle, die standartmäßig von Gradle mitgelifert werden:

```ad-note
collapse: true
title: Output

Build Setup tasks
-----------------
init - Initializes a new Gradle build.
wrapper - Generates Gradle wrapper files.

Help tasks
----------
buildEnvironment - Displays all buildscript dependencies declared in root project 'cleanprojeect'.
dependencies - Displays all dependencies declared in root project 'cleanprojeect'.
dependencyInsight - Displays the insight into a specific dependency in root project 'cleanprojeect'.
help - Displays a help message.
javaToolchains - Displays the detected java toolchains.
outgoingVariants - Displays the outgoing variants of root project 'cleanprojeect'.
projects - Displays the sub-projects of root project 'cleanprojeect'.
properties - Displays the properties of root project 'cleanprojeect'.
resolvableConfigurations - Displays the configurations that can be resolved in root project 'cleanprojeect'.
tasks - Displays the tasks runnable from root project 'cleanprojeect'.
```