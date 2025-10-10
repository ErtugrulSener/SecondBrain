## OAuth2 Flow
- Sichtbare und Unsichtbare Schritte um Informationen auszutauschen

1. Der *Resource Owner* (Ich) möchte einem *Client* (gmail.com) ermöglichen, in meinem Namen einen weiteren Service (Github) zu erreichen
2. Der *Client* sendet eine Anfrage an den *Authorization Server* mit folgenden Dingen:
	1. Client ID
	2. Redirect URI
	3. Response Type
	4. Scope
3. Der *Authorization Server* verifiziert, ob bereits eine aktive Session besteht (ob ich bereits authentifiziert bin)
	1. Falls nicht, dann öffnet er einen Login
	2. Falls authentifiziert, öffnet er eine Maske, in der der *Resource Owner* explizit den Zugriff samt Scopes erlauben muss
4. Der *Authorization Server* macht einen *Redirect* zu der *Redirect URI* (zurück zum *Client*), zusammen mit dem temporären *Authorization Code*
5. Der *Client* kontaktiert den *Authorization Server direkt* mit folgenden Dingen:
	1. Authorization Code (Aus Schritt 4)
	2. Client ID
	3. Client Secret
6. Der *Authorization Server* verifiziert die Daten und gibt einen *Access Token* zurück
7. Der *Client* nutzt den *Access Token* für die Authentifizierung bei dem *Resource Server*