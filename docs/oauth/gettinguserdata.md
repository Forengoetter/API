Um die Nutzerdaten zu erhalten ist ein sogenannter _token_ nötig. Dieser wird als `GET` Parameter an deine Weiterleitungs URL angehängt.
**Beachte:** Dieser Wert kann auch _denied_ sein, wenn der Benutzer die Berechtigung **nicht** erteilt hat.

Der Nutzer wird nachdem er die Berechtigung erteilt hat auf deine Weiterleitungs URL weitergeleitet. Hierbei wird der  `referer` wenn möglich versteckt. Um auf die Seite zum erteilen der Berechtigungen zu gelangen ist eine **einmalige** URL nötig. Diese setzt sich aus folgenden `GET` Parametern zusammen:

| Parametername | Wert                                                                                                                                                |
| ------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| applicationID | deine Anwendungs ID                                                                                                                                 |
| client_id     | dein öffentlicher Schlüssel                                                                                                                         |
| redirectURL   | deine Weiterleitungs URL                                                                                                                            |
| scope         | die Daten welche du erhalten möchtest, per **,** getrennt. Valide Werte sind: `username`, `email`, `avatar`, `minecraft_username`, `minecraft_uuid` |

Eine URL könnte also so aussehen:
`https://forengoetter.org/oauth/?applicationID=1&client_id=mypublickey&redirectURL=mypage.net&scope=email`


Der nun erhaltene _token_ muss dann **innerhalb von 5 Minuten** an den Endpunkt `https://api.forengoetter.org/oauth` gesendet werden, da jeder _token_ nur **5 Minuten** gültig ist. Hierfür müssen einige Parameter gesetzt sein, mehr über diese findest du im Abschnitt _Parameter_.
Dieser Entpunkt gibt wie alle unsere Schnittstellen die Daten im **JSON** Format zurück.
Eine erfolgreiche Antwort könnte so aussehen:
```
{
    "type": "success",
	"userData": {
		"email": "mymail@example.net"
	}
}
```
Sollte der Typ dieser Antwort `error` sein, wird ebenfalls ein `code` (ebenfalls als **HTTP-Response Code**) und ein Parameter `message` gesendet.
Ein beispiel könnte so aussehen:
```
{
	"type": "error",
	"code": 400,
	"message": "secret key not set"
}
```
