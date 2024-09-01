# 1. Konzept): Skripting-Sprache
- Groovy ist eine Skriptingsprache, die auch in der JVM läuft
	- Ergo: Groovy erzeugt am Ende Bytecode, genauso wie Java - Die dann von der JVM interpretiert wird.
- Baut auf Java auf, erlaubt schnellere Entwicklung

# 2. Konzept): Klammern sind optional
- wenn eine Funktion genau einen oder mehrere Argumente akzeptiert
- ```println 'bracket-free'``` und ```println('bracket-free')``` ist das Selbe

# 3. Konzept): Support für Closures
- Funktion als Variable
- Das equvivalent zu Lambda-Ausdrücken aus Python / Java

```Groovy
def amazingCalculator = { a, b -> a + b }
println amazingCalculator(2, 3) // prints 5
```