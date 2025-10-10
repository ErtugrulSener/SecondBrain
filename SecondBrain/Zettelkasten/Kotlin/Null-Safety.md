Einer der größten Features von Kotlin ist Null-Safety. Folgendes Programm würde zum Beispiel nicht kompilieren:

```Kotlin
var brand: String? = null  
println(brand.uppercase())
```

Stattdessen muss man explizit den null-Case behandeln, so zum Beispiel:

```Kotlin
var brand: String? = null  
println(brand?.uppercase())
```