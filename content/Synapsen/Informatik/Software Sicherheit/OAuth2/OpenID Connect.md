## OAuth2 nur für die Authentifizierung
- OAuth2 gibt der Applikation nur einen Schlüssel
- OIDC ist ein Layer, der auf *OAuth2* basiert und Funktionalitäten die Authorisierung bietet

## Unterschiede zu OAuth2
- OIDC gibt dem Client einen eine Art Badge, wo etwas mehr Informationen drin stecken als bei dem JWT Token
	- Id Number
	- Logged In
	- Expiration
- Der Flow sieht aus wie bei [[Flow|OAuth2]] mit folgenden Unterschieden
	- Bei Schritt 2 sendet der Client zusätzlich noch einen *Scope* namens *openid* mit, damit der *Authorization Server* weiß, was er zutun hat
	- Bei Schritt 6 sendet der *Authorization Server* neben dem *Access Token* noch einen *ID Token* zurück

## ID-Token
- Ist ein JWT
- Enthält sogenannte *Claims*

## Claims
- Die einzelnen Informationen (Daten) im ID-Token
- Ergo:
	- Issued By
	- Issued At
	- Expiration
	- User Id
	- E-Mail

## Vorteile
- SSO (Ein Login auf einer Applikation, kann bei einer anderen Seite wiederverwendet werden)