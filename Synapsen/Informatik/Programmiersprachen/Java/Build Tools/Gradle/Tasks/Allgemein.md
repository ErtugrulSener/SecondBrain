# Der Gradle Task Graph
Gradle Tasks wie "build" können von anderen Tasks wie "assemble" und "check" abhängen. Dadurch bildet sich ein Dependency Graph und eine Reihe von Tasks, die Gradle abarbeiten muss. Auch genannt: "Gradle Task Graph".

# Aufbau eines Tasks
Ein Task besteht immer aus:

Hier am Beispiel von "compileJava":
- Input (z.B: Source Dateien, aber auch Build Konfigurationseinstellungen)
- Action (z.B: Erzeugen von Class Dateien)
- Output (z.B: Die Class Dateien, die später von der JVM interpretiert werden)

# Struktur innerhalb eines Tasks
1) Configuration Area
Alles was nicht in "doFirst" oder "doLast" steht wird in der Konfigurationsphase ausgeführt.

2) Action Area
Alles was in "doFirst" oder "doLast" steht, wird in der Ausführung ausgeführt, das sind so 90% aller Dinge, die wir machen wollen behaupt ich.

```Groovy
tasks.register("myNewTask") {
	// 1) Configuration Area
	myConf = 1

	// 2) Action Area
	doLast {
		println "I'm Done with my job!"
	}
}
```

# Beschreibung für Task hinzufügen
## description
Innerhalb eines Tasks gibt es die "description" Methode, der man einen Text hinzufügen kann, um seinem Custom Task eine Beschreibung als Helpmessage zu verpassen.

```Groovy
task afterTest {  
    description = 'hey'
    println 'Run after test'
}
```

## group
Um die Gruppe dieses Tasks zu spezifizieren (default=other) muss man einfach die "group" Methode aufrufen.

```Groovy
task afterTest {  
    group = 'java'
    println 'Run after test'
}
```


# Outcome Labels
Ein Task kann folgende Label tragen:
- (no label) or EXECUTED (ist das Selbe)
Der Task wurde erfolgreich ausgeführt.

- FROM-CACHE
- SKIPPED
Task wurde explizit übersprungen über die CLI.
Das ```onlyIf``` Prädikat hat false returned.

- NO-SOURCE
Es wurde kein Input gefunden, skip den Task.

- UP-TO-DATE
Incremental Build bzw. Caching von Gradle verhindert das doppelte ausführen des Tasks, weil keine Änderungen seit dem letzten Mal gemacht wurden. Der Output wäre der Selbe.

siehe: [Docs](https://docs.gradle.org/current/userguide/more_about_tasks.html#sec:task_outcomes)

# Woher kommen die Tasks, die nicht standartmäßig mitgeliefert werden?
Sie sind Konfigurationen aus den [[plugins]], die wir spezifizieren im [[build.gradle]] Skript.

# Unvollständige Liste der wichtigsten Plugins

| Name         | Beschreibung                                                                                                                             |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------- |
| base         | Dieses Plugin stammt von Core Gradle und bringt Tasks wie "assemble" und "build".                                                        |
| java-library | Plugin für eine java library, bringt tasks mit denen man Source Code kompilieren kann (compileJava) oder eine jar Datei erstellen (jar). |
| application  | Plugin für eine Applikation, braucht zu den Dingen aus dem java-library Plugin nun noch eine Mainklasse, die ausgeführt werden soll. Bringt tasks um die Software auszuführen wie "run".                                                                                                                                        |
