## Spécification du fichier de configuration `network.json`

### `[CONF_REQ_FILE_ANAS_0010_00]` - Emplacement du fichier de configuration
Le fichier de configuration `network.json` doit être situé dans le répertoire `C:\Users\UF...\conf\` sous Windows, et dans /etc/panduza/ sous Linux.

### `[CONF_REQ_FILE_ANAS_0020_00]` - Format du fichier de configuration
Le fichier de configuration `network.json` doit être au format JSON.

### `[CONF_REQ_FILE_ANAS_0030_00]` - Contenu du fichier de configuration
Le fichier de configuration `network.json` doit contenir les informations suivantes :

| Champ | Description | Type | Obligatoire |
| --- | --- | --- | --- |
| `BROKER_HOST` | Adresse IP du broker MQTT | String | Oui |
| `BROKER_PORT` | Port du broker MQTT | Integer | Oui |
| `API_HOST` | Adresse IP de l'API Flask | String | Oui |
| `API_PORT` | Port de l'API Flask | Integer | Oui |

### `[CONF_REQ_FILE_ANAS_0040_00]` - Gestion des erreurs
- Si le fichier de configuration `network.json` n'existe pas, l'application doit journaliser une erreur et retourner un code d'erreur 500.
- En cas d'erreur lors de la lecture ou de l'écriture du fichier de configuration, l'application doit journaliser l'erreur et retourner un code d'erreur 500.

