- Zunächst werden alle [[Lifecycle Annotations#@PreDestroy]]  Annotationen aufgerufen
- Danach werden die Beans released, um vom GC zerstört zu werden

```ad-note
Achtung: Bei Beans mit dem Scope 'prototype' ist Schritt 1 mit @PreDestroy nicht möglich, wir wissen nicht wann diese aufgeräumt werden sollen.
```