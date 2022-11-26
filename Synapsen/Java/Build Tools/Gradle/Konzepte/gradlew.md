Der Gradle Wrapper (gradlew) wird jeweils als Batch (.bat) und Shell Datei ausgeliefert und heißt "gradlew".

# VCS
Die Datei wird mit versioniert.

# Vorteile
- Jeder, der mein Projekt bauen möchte - Benötigt nur mein Projekt selbst. Der Gradle Wrapper wird beim Aufruf prüfen, ob ich Gradle bereits installiert habe und falls nicht, lädt er Gradle selbstständig herunter.

- Der Wrapper beinhält eine bestimmte Version von Gradle. Falls das nicht mit der Version vom systemweiten gradle zusammenpasst, lädt der Wrapper meine spezifische Version herunter.

- Danach macht Gradle die restlichen magischen Schritte wie meine Dependencies runterzuladen usw. Zusammen sind diese beiden Konzepte ein "Fire and go" Befehl um ein Projekt zu bauen.