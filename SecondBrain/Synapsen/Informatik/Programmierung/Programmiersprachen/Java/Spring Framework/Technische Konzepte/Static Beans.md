```Java
public static BeanInterface myBean() {
	return new BeanImpl();
}
```

- Static-Beans werden erstellt, bevor andere Beans initialisiert werden. Sie haben Vorrang.
- z.B: nötig für [[1-Initialisierung#a) Bean-Definitionen laden]]