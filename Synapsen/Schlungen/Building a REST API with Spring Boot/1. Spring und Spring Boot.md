## Spring vs. Spring Boot
Gemeinsamkeiten:
- Beides sind Frameworks
- IOC aus Spring Core wird in beiden verwendet

Unterschiede:
- Spring ist eine große Toolbox, braucht viel Konfiguration. Spring Boot dagegen ist vor konfiguriert.
- Spring Boot kommt mit einem Embedded Web Server (um etwas Lauffähiges zu haben und nicht erst selbst deployen zu müssen)

## Warum Spring Boot und nicht Spring?
Das Spring Framework bietet quasi alle möglichen Funktionalitäten für die Applikationsentwicklung. Dafür muss man aber auch einiges an Konfiguration selbst machen.

*Spring Boot* dagegen nimmt einem diese Arbeit ab, viele Dependencies (die man häufig benötigt), sind hinter den sogenannten "Starter" Dependencies versteckt. Viele Konfigurationen werden für einen bereits gemacht.

Außerdem ist der Embedded Web Server hilfreich für schnelles Bootstrapping.

## Spring's IOC Container
- aus dem Modul Spring Core

*IOC* steht für *Inversion of Control* und wird vom Spring / Spring Boot Framework sehr exzessiv genutzt.

Es ist explizit nicht das Selbe wie die *Dependency Injection*, die *DI* ist nur eine Art "Werkzeug" wie das Prinzip von *IOC* funktioniert bzw. wie man externe Abhängigkeiten zur Laufzeit erzeugt und in die Klassen, die sie benötigen, bekommt.

*Beispiel Use Case*:
Für die Produktion soll eine andere Datenbank benutzt werden als für die lokale Entwicklung.

## Spring Initializr
Eine schöne und einfache Methode eine Spring Boot Anwendung generieren zu lassen. Siehe [Hier](https://start.spring.io/)