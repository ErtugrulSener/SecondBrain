## @Scope("singleton") - (Default)
- Die Komponente wird ein Mal erstellt von Spring
- Wird danach gecacht
- Achtung vor *Multi-Threading*
	- nutze sie Stateless oder Immutable Beans
	- nutze `synchonized`
	- nutze einen anderen Scope

## @Scope("prototype")
- Neue Instanz, jedes Mal wenn wir diese Bean brauchen
- Achtung: `context.getBean()` - gibt dir JEDES Mal eine neue Instanz

## @Scope("session")
- Neue Instanz pro User Session

## @Scope("request")
- Neue Instanz pro Request

## Sonstige
- Web Socket scope
- Refresh scope
- Thread scope
- (Eigenst geschriebener) Custom scope
	- implementiert Scope Interface