# Historischer Background
Software wächst mit der Zeit und so wachsen auch die Build Laufzeiten. Früher konnte so ein Buildprozess sogar mehrere Stunden dauern. Der "Fail Fast" Ansatz war absolut noch kein Thema in der Welt der Softwareentwicklung.

# Build Lifecycle
Ein Build besteht aus einer Sequenz von Tasks. Tasks bestehen aus:
- Input
- Action
- Output

So ist ein Output eines Tasks der Input für den nächsten Task usw.

# Allgemein
## Inkrementelle Builds
Einen Build Cache zu nutzen bedeutet, dass wenn der Input eines Tasks sich nicht verändert hat, das man dann einfach den letzten Output verwendet.

Natürlich müssen die Tasks dafür *deterministisch* sein. Außerdem wird wirklich nur der letzte Buildoutput gesichert.

## Local Cache
Es wird lokal eine Datenbank angelegt, in der der Output gecacht wird. Dies wird für N Builds gemacht, sodass man auch auf Buildergebnisse des fünftletzten Builds zugreifen kann.

```ad-note
Wenn man Dinge im Cache sucht und findet nennt man es "Cache Hit", wnen man es nicht findet "Cache Miss".

Bei einem Cache Miss, müsste die Aktion erneut ausgeführt werden.
```

## Remote Cache
Zusätzlich zum Local Cache gibt es nun noch einen Remote Cache. Wir schauen erst im Remote Cache nach einem Hit. Wenn nicht, dann führt man die Aktion durch und lädt sie im Remote hoch, damit andere dieses nutzen können.

Große Firmen wie Microsoft und Google nutzen diese Technologie bereits für sich.
Sie ist ein Local Cache, der Remote gespeichert und verteilt wird.

# Sollten wir den Remote Build Cache immer nutzen?
Nein, vor allem wenn das Herunterladen des Build Cache vom Remote länger dauert, als die Action gebraucht hätte. Beispiel:

Meine Tests laufen in 3 Sekunden, den Build Cache für den test Task herunterzuladen braucht durch ein langsames Netz aber 12 Sekunden. Damit verlangsamt der Build Cache sogar das Development.

# Rolle von Gradle
Gradle hat über die Zeit immer mehr Cache Methoden eingefügt, genau in der Reihenfolge oben (Erste inkrementelle Builds, dann Local Cache und später Remote Cache).

## Phase 1: Inkrementelle Builds
1) Gradle cacht den Output von Tasks nach der Action sowie den dazugehörigen Input als Hash. Man mappt Hash -> Output.
2) Sollte beim nächsten Mal der Hash des neuen Inputs genau dieser aus 1) sein, dann findet ein Cache Hit statt.
3) Man erhält für diesen Task das Output Label "UP-TO-DATE". Siehe auch [[Synapsen/Informatik/Programmiersprachen/Java/Build Tools/Gradle/Tasks/Allgemein#Outcome Labels|Outcome Labels]]

Die Limitierungen dieser Phase der Builds sind klar:
- Clean Build
- Branches wechseln

## Phase 2: Local Cache
Wir speichern ein Mapping von Inputs zu Outputs, wie beim inkementellen Build. Diesmal haben wir eben mehrere Einträge in unserer "lokalen Datenbank" auf dem Filesystem. Dies kommt mit einem Preis an Speicherplatz. Bei vielen Projekten kann dieser Cache sehr groß werden bis zu mehreren hunderten MB.

Gradle schaut zunächst in den Build Ordner und sieht, ob er den Output bereits im vorherigen Build hatte. Der Local Cache Support kommt also "on top" auf dem inkrementellen Build aus Phase 1.

### Local Cache aktivieren
Nun zeige ich einige Wege, wie man den Local Build Cache aktiviert.

### über CLI
```Bash
./gradlew.bat --build-cache

## Debug
./gradlew.bat -i
```

### über gradle.properties
```properties
org.gradle.caching=true

## Debug
org.gradle.caching.debug=true
```

### Ungenutzte Cache Entries löschen
settings.gradle
```Groovy
buildCache {  
    local {  
        removeUnusedEntriesAfterDays = 30  
    }  
}
```

Wo befindet sich nun dieser Local Cache?
(default) Unter: *~/.gradle/caches/build-cache-1*

Die Limitierungen dieser Phase der Builds sind klar:
- Kann nur auf Output von lokalen Builds referenzieren
- First Build
- Sich often veränderndes großes Projekt (Wo man oft pullt)
- Man kommt vom Urlaub zurück

## Phase 3: Remote Cache
Der letzte Ort an dem die Cache Entries gesucht werden, ist der Remote Cache. Folgende kann man ihn aktivieren:

```Kotlin
buildCache {  
    local {  
        removeUnusedEntriesAfterDays = 30  
    }  
    remote<HttpBuildCache> {
	    url = uri("https://enterprise-training.gradle.com/cache/")
	    credentials {
		    username = System.getenv("CACHE_USERNAME")
		    password = System.getenv("CACHE_USERNAME")
	    }
	    isPush = true
    }
}
```

### Sharing Strategie
Man könnte die Developer als "Consumer" betrachten, nur die CI Maschine pusht den Cache.

```Kotlin
val isCiServer = System.getenv().containsKey("CI")

buildCache {
	local {
	...
	}
	remote<HttpBuildCache> {
		...
		isPush = isCiServer
	}
}
```

### Docker-Image für den Remote Cache Node
[Link](https://hub.docker.com/r/gradle/build-cache-node/)

# Caching Optionen in Tasks
Das Caching ist für alle Built In Tasks aus [[Built-In Tasks]] bereits aktiv.

## Caching Support für Custom Tasks aktivieren
```Kotlin
tasks.named("zipTestResult") {
	outputs.cacheIf { true }
	inputs.files(tasks.test)
}
```

## Inputs und Outputs spezifizieren
```Kotlin
tasks.register<Exec>("helloFile") {
	workingDir = layout.buildDirectory.asFile.get()
	commandLine("bash", "-c", "person=`cat ../name.txt`; echo \"hello \$person\" > hello.txt")

	outputs.cacheIf { true }

	inputs.file(layout.projectDirectory.file("name.txt"))
	.withPropertyName("helloInput")
	.withPathSensitivity(PathSensitivity.RELATIVE)

	outputs.file(layout.buildDirectory.file("hello.txt"))
	.withPropertyName("helloOutput")
}
```

## Input Properties spezifizieren um Caching zu beeinflussen
```Kotlin
tasks.register<Generate>("generate") {
	inputs.property("hostName", InetAddress.getLocalHost().hostName)
	inputs.property("hostAddress", InetAddress.getLocalHost().hostAddress)
}
```

# Cache Misses
## Nichtdeterministischer Input in Dependency vom Subprojekt
Nichtdeterministischer Input lässt sich nicht so gut cachen, für das Caching kann man die Datei ignorieren.

```Kotlin
normalization {
	runtimeClasspath {
		metaInf {
			ignoreAttribute("Implementation-Timestamp")
		}
	}
}
```

# Troubleshooting Cache Misses
● Task not caching properly?
	○ Check cache key differences
	○ Build scan or Gradle Enterprise insights
● Possible issues:
	○ Absolute paths instead of relative
	○ Inputs contain timestamps
	○ Collection input has non-deterministic ordering
	○ Overlapping outputs
	○ External inputs, eg. system properties
	○ File encoding
	○ Line endings
	○ Symlinks
	○ Java version
		■ Default behavior only tracks major version
		■ Recommend using toolchains