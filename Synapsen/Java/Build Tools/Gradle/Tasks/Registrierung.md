# Neue Tasks: task.create vs. task.register
Beim Register Befehl wird der Task nur registriert, aber nicht immer ausgeführt. Beim "create" wird der Task auch verarbeitet (interpretiert) wenn er einfach nur von Gradle gelesen wird. Dabei werden Print Statements ausgeführt.

Task.create und "eager Tasks" (ohne irgendeinen Befehl, findet man in Groovy DSL) sind Legacy und sollten nicht benutzt werden.

# Vorhandene Tasks: task.named vs. eager Tasks
Eigentlich selbsterklärend, lieber das nutzen aus dem selben Grund wie oben

# Zusätzlicher Vorteil:
- Bessere Performance in der Konfigurationsphase ([[Gradle Build Lifecycles#2: Configuration]])