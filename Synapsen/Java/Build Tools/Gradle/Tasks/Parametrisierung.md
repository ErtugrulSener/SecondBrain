# Parametrisierung über CLI
Um über CLI einen Parameter in Gradle zu nutzen kann man -Pkey=value nutzen. Im Code kann man dann so drauf zugreifen:

```Groovy
task afterTest {  
    group = 'java'

	val value = providers.gradleProperty("key").orElse("alternative value");

    println "$value"
}
```
