```Kotlin
when (age) {
	in 13 .. 19 -> println("Teenager")
	!in 0 .. 12 -> println(...)
	else -> println(...)
}
```