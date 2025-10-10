- Die Plain JDBC Api ist sehr error prone, für eine Zeile Business Logik braucht es etwa 10 Zeilen Boilerplate Code
![[error-prone-jdbc.png]]

## JdbcTemplate
- Jede Instanz braucht eine DataSource und baut eine Verbindung zur Datenbank auf + Es ist Thread Safe!
	- Ergo: *Eine Instanz sollte mehrfach genutzt werden*
- Lösung dafür ist die JdbcTemplate Klasse
	- Implementiert das Template Design Pattern
- Siehe auch *RestTemplate*, *JmsTemplate*, *WebServiceTemplate* usw.

## JdbcTemplate::queryForObject
- Kümmert sich um Error Handling
- Um die Verbindung (Auf und Abbau)
- Ausführen des Statements
- Result Set in Objekt konvertieren usw.

## RowMapper
- Um jede Zeile des Results auszulesen und etwas damit zu tun (mappen)
- Den Prozess nennt man *Callback*