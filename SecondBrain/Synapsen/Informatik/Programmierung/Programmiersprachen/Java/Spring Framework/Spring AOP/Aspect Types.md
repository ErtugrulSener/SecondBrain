- 5 Aspekttypen

## @Before
- Vor dem Target wird dieser Code ausgeführt (z.B: für Security Checks)

## @AfterReturning
- Gegenteil von @Before
- Es gab keine Exception

## @AfterThrowing
- Es wurde eine Exception geschmissen

## @After
- Egal ob Exception geschmissen wird, oder nicht

## @Around
- Before & After zusammen
- ist etwas gefähhrlich, man muss selbst den Aufruf des Targets übernehmen
	- wenn man das vergisst, passiert nichts