# Java Bean
Vorab:
Eine Java Bean ist eine ganz normale Javaklasse, nur mit der Bedingung das sie gewisse Konventionen befolgen muss.

# Wie zeichnet sich eine Java Bean aus?
- Java Beans sind [[POJO]]'s (Plain Old Java Objects)
- Eine Java Bean Klasse ist eine Klasse dessen Felder privat sind und nur über die Getter bzw. Setter erreichbar sind. Auch genannt: "accessor" und "mutator" Methods.
- Außerdem besitzt sie einen public, no arg constructor (den Default Constructor)
	- (Er darf natürlich auch weitere Constructors besitzen)

- (optional) Außerdem sollte die Java Bean Klasse das @Serializable Interface implementieren, so erkennen Framework's diese Klasse als "serialisierbarer Container von Daten".

# Der Nutzen von Java Beans
- Trennung von Business Logik (die Daten in den Feldern) und demjenigen, der die Daten erhält (durch Getter)
- Das macht sowas wie Mocking für die Methode der Java Bean Klasse überhaupt erst möglich. Bei Feldern müsste man schon relativ umständlich mit Reflection hantieren um die Inhalte in Runtime auszutauschen.

# Unterschiede zu Spring Beans
- Sie sind nicht von Spring in irgendeiner Art und weise gemanaged wie [[Spring Bean|Spring Beans]].