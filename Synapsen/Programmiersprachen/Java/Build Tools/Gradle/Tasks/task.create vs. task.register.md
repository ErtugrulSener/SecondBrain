# Neue Tasks: task.create vs. task.register
Bei der "task.create" Methode  wird der Task auch verarbeitet (interpretiert) wenn er einfach nur von Gradle gelesen wird. Dabei werden Print Statements ausgeführt. Das gillt für z.B: alle Print-Befehle die in der Configuration Area von Tasks stehen.

```ad-note
Task.create und "eager Tasks" (ohne irgendeinen Befehl, findet man in Groovy DSL) sind Legacy und sollten nicht benutzt werden.
```

# Vorhandene Tasks: task.named vs. eager Tasks
Eigentlich selbsterklärend, lieber "task.named" nutzen aus dem selben Grund wie oben

# Vorteil:
- Bessere Performance in der Konfigurationsphase ([[Gradle Build Lifecycles#2: Configuration]])
- Kein Ausführen von Print Statements ohne es zu beabsichtigen
- Die Methoden sind legacy, sie könnten in Zukunft entfernt werden