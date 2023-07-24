```Java
	@Before
	public void trackChange(JoinPoint joinPoint) {
		// joinPoint.getSignature().getName();
	}
```

Für mehr Informationen siehe [[Join Point]]]

## JoinPoint Expressions
### Template
`execution(<method pattern>`

### Verknüpfung
`execution(<pattern1>) || execution(<pattern2>)`

### Method Pattern
[Modifiers] ReturnType [ClassType] MethodName (Arguments) [throws ExceptionType]

### Wildcards
- `*` matcht einen (return type, package usw.)
- `..` matcht null oder mehr (argumente oder packages)
	- man kann nicht mit .. in *packages* anfangen
	- Dann nutzt man eher `*..`