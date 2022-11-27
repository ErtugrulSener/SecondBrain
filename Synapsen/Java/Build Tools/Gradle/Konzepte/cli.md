# Logging Optionen
## Mehr Konsolenoutput von Gradle erhalten

```Bash
./gradlew.bat :app:test --console=verbose
```

Stattdessen kann man auch in der gradle.properties folgendes definieren:

```Ini
org.gradle.console=verbose
```

## Dry run (was wäre wenn?)

```Bash
./gradlew.bat :app:test --dry-run
```

## Lognachrichten verstecken, nur der Output von Tasks ist sichtbar

```Bash
./gradlew.bat :app:test -q
```