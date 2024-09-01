# Totschlagargument für den Gradle Wrapper
"Was ist, wenn du mehrere Projekte auf dem System hast, die alle mit einer unterschiedlichen Gradle Version gebaut werden müssen, weil sonst ein anderes Build entsteht?"
- Natürlich könnte man zu jedem Build ein Skript schreiben und vorher den PATH ändern bzw. den Pfad zu Gradle angeben.. bzw. GRADLE_HOME
- Oder man muss jeden Befehl mit einem expliziten Pfad machen (/usr/bin/gradle6.5/...)

Jetzt muss aber jeder Developer auch sich um diese Struktur auf seinem Rechner kümmern... Pfadkonflikte Hura!

Der Gradle Wrapper (gradlew) wird jeweils als Batch (.bat) und Shell Datei ausgeliefert und heißt "gradlew".

# VCS
Die Datei wird mit versioniert.

# Vorteile
- Jeder, der mein Projekt bauen möchte - Benötigt nur mein Projekt selbst. Der Gradle Wrapper wird beim Aufruf prüfen, ob ich Gradle bereits installiert habe und falls nicht, lädt er Gradle selbstständig herunter.

- Der Wrapper beinhält eine bestimmte Version von Gradle. Falls das nicht mit der Version vom systemweiten gradle zusammenpasst, lädt der Wrapper meine spezifische Version herunter.

- Danach macht Gradle die restlichen magischen Schritte wie meine Dependencies runterzuladen usw. Zusammen sind diese beiden Konzepte ein "Fire and go" Befehl um ein Projekt zu bauen.

# Welche Gradle Wrapper Version nutze ich?
Dafür einfach unter "gradle/wrapper/gradle-wrapper.properties" nachschauen. Folgend sieht das aus:

![[gradle-wrapper-properties.png]]

# Distributionen
- bin = binary only
	- Kleiner in der Größe, gut für Buildmaschinen
- all = binary + sources
	- Gut für IDE's

Die Gradle Distributionen werden gespeichert unter: *~/.gradle/wrapper/dists/*