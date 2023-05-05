Gradle hat eine Art der Konfigurationen aus Phase 2 [[Gradle Build Lifecycles#2: Configuration]] namens SourceSets.

# Java Plugin
Beim Java Plugin werden dadurch z.B: folgende Pfade standartmäßig initialisiert bzw. den SourceSets hinzugefügt:

- src/main/java
- src/test/java

## Weitere SourceSets hinzufügen

```Groovy
sourceSets {
	main {
		java {
			srcDir("src/java")
		}	
	}
}
```