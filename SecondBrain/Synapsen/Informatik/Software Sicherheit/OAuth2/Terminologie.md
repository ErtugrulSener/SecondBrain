## Resource Owner
- Der User

## Client
- Die Applikation (z.B: eine Webseite)

## Authorization Server
- Der Server, der den Resource Owner kennt
- Hier sollte der Selbige einen Account haben

## Resource Server
- Die API / Der Service, den der Client (die Webseite) für den Resource Owner benutzen möchte

## Redirect URI (Callback Url)
- Der Authorization Server leitet den Resource Owner zurück auf diese Seite, nach dem die Berechtigung erteilt wurde

## Response Type
- Der Typ von Informationen, den der Client vom Resource Server möchte

## Scope
- Die Berechtigungen, die der Client möchte

## Consent
- Der Authorization Server nimmt die Scopes, die der Client möchte und zeigt sie ihm an bei der Anfrage beim Resource Server

## Client ID
- Wird benutzt, um den Client mit dem Authorization Server zu identifizieren

## Client Secret
- Ein geheimes Passwort, was nur der Client und der Authorization Server kennen

## Authorization Code
- Ein kurzlebiger temporärer Code, den der Authorization Server an den Client sendet
- Der Client sendet das zurück an den Authorization Server + Client Secret
- Dafür bekommt er den *Access Token*

## Access Token
- Der Schlüssel, den der Client nutzt um mit einem Resource Server zu sprechen