## Initiales Projekt erstellen
Um ein initiales Projekt zu erstellen, nutzen wir das Tool ```npx``` (node package executor):

```shell
npx @vaadin/cli init --preset hilla-quickstart-tutorial hello-world
```

## Applikation starten
Um die Applikation zu starten nutzen wir den Maven Wrapper (mvnw) im generierten Ordner:

```shell
./mvnw
```

Dies startet die inkludierte Spring Boot Applikation und macht ihn erreichbar unter localhost:8080. Hier eine kleine Erklärung zu den generierten Ordnern und Dateien:

- *frontend* - In dem Ordner 