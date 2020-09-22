Bei dieser Schnittstelle variieren die Rückgabewerte ja nach Erfolg der Anfrage.

### Rückgabewerte bei einer erfolgreichen Anfrage
| Rückgabename | Beschreibung                                                                                                               |
| ------------ | -------------------------------------------------------------------------------------------------------------------------- |
| type         | Dieser Wert ist immer gesetzt, bei erfolgreichen Anfragen, ist dieser immer **success**.                                   |
| userData     | Dieses Objekt sind die jeweiligen Daten des Benutzers, die Schlüssel dieses Objektes entsprechen den **scope** Parametern. |

### Rückgabewerte bei einer fehlerhaften Anfrage
| Rückgabename | Beschreibung                                                                                    |
| ------------ | ----------------------------------------------------------------------------------------------- |
| type         | Dieser Wert ist immer gesetzt, bei fehlerhaften Anfragen, ist dieser immer **error**.           |
| code         | Der passende **HTTP-Code** zu diesem Fehler, dieser wird auch als `Response Code` gesetzt.      |
| message      | Eine kurze Beschreibung des aufgetretenen Fehlers, da der Fehlercode nicht immer eindeutig ist. |
