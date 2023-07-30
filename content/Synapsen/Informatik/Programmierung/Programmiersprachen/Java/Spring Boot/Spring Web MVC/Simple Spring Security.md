# Authentifikation
## Principal als Synonym für User
Wir nutzen *Principal* als Synonym für den *User*, weil der Nutzer am Ende sowohl menschlich als auch maschinell sein kann.

## Basic Authentication
Der einfachste Weg der Authentifikation ist über die *Credentials* des *Principal*. Dies nennt sich dann die *Basic Authentication*.

## Authentication Session
Normalerweise müsste der User bei jedem Request seine Credentials erneut angeben und der Server sie verifizieren, dies wäre (vor allem für den Server) sehr aufwendig.

Daher nutzt man *Session Token*, die der User in einem *Cookie* mit sendet. Cookies werden automatisch an den Server gesendet, der Server validiert diesen Cookie - indem er in die Datenbank schaut und den User dafür versucht zu finden.

# Autorisation
Die Autorisation ist der nächste Schritt, bei der geht es um die Berechtigungsprüfung für den User.

## RBAC (Role Based Access Control)
Spring bietet die Autorisation mittels RBAC. Das bedeutet, dass der *Principal* eine Anzahl an *Rollen* hat. Jede *Ressource* spezifiziert welche *Rolle* ein *Principal* haben muss, um diese Aktion nach entsprechender Authentifikation auszuführen.

Beispiel:
- Ein *Principal* mit der *Administrator* Rolle ist meist autorisiert, jede Aktion auszuführen. 

RBAC kann auf Methodenlevel oder global konfiguriert werden.

## SOP (Same Origin Policy)
Die einfachste aller Securitymaßnahmen ist die SOP, die besagt das nur Skripte einer bestimmten Webseite von dem Backend akzeptiert werden. Wenn also jemand die Auth Cookies klaut und versucht extern irgendwas ans Backend zu bringen, wird das abgelehnt.

Natürlich ist das kein allumfassender Schutz, denn man kann auch Skripte über Code Injection durch die Webseite ans Backend bringen, aber es ist einer der wichtigsten Maßnahmen.

## CORS (Cross Origin Request Sharing)
Der Server kann die Regel von SOP etwas aufweichen, indem er verschiedene *allowed origins* spezifiziert, die mit ihm kommunizieren dürfen.

In Spring nutzt man dafür die `@CrossOrigin` Annotation.