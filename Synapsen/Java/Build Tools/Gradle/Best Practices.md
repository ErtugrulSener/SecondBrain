1) Immer den Gradle Wrapper nutzen
2) Das .gradle - Verzeichnis gehört nicht in die VCS
3) Führe gradle.init in einem eigenen Ordner aus
4) Wenn du die Groovy DSL für deine Gradle Builds nutzt, solltest du in den Gradle Wrapper Konfigurationen die Gradle distribution auf "all" stellen
5) Es ist empfohlen, immer mindestens ein Subprojekt zu haben. Standartmäßig nennt Gradle das "app"
6) Gradle wird in der Konfigurationsphase alle [[build.gradle]] Dateien parsen, daher bietet es sich an immer das Projekt mitzugeben wenn man einen Task ausführt: "./gradlew :app:run"