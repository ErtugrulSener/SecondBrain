# Was ist Gradle?
Gradle ist Build Automationstool.

Das bedeutet:
- Code in Packages zu einer Deployable Unit zusammenpacken
- Große und kleinere Projekte bearbeiten
- Tests ausführen
- Resourcen managen
- Build (Deployable Unit) auf einen Server deployen

# Warum sollte ich Gradle nutzen?
- Gradle wurde entwickelt, um andere Applikationen zu bauen und auszuführen
- Lässt sich einfach konfigurieren
- Im Gegensatz zu Maven, ist es weniger verbos
- gradlew erlaubt Nutzung von Gradle out of the box
- Sehr performant, inkrementelle Builds

# Abhängigkeiten
- Gradle wurde in Java geschrieben, zur Ausführung braucht man *JDK 8 oder höher*

# Konzepte
- [[build.gradle]] - Die Gradle Build Skript Datei, equivalent der pom.xml von Maven
- [[Tasks]] - Definiert eine Unit, kann von der Kommandozeile aufgerufen werden über den Namen
- [[gradlew]] - Ein Skript, dass man aufrufen kann um Gradle Builds auszuführen. Es lädt Gradle in der benötigten Version runter, falls es nicht schon auf dem System existiert. Es ermöglicht auch Environment Variablen für den Build zu setzen. Oder auch JVM Variablen.