## Specification of the `network.json` configuration file

### `[CONF_REQ_FILE_NET_0010_00]` - Location and format of the configuration file
Windows Path : `C:\Users\UF...\conf\` 

Linux Path : /etc/panduza/ 

The `network.json` configuration file must be in JSON format.

### `[CONF_REQ_FILE_NET_0020_00]` - Content of the configuration file
The `network.json` configuration file must contain the following information:

| Field | Description | Type | Required |
| --- | --- | --- | --- |
| `BROKER_HOST` | MQTT broker IP address | String | Yes |
| `BROKER_PORT` | MQTT broker port | Integer | Yes |
| `API_HOST` | Flask API IP address | String | Yes |
| `API_PORT` | Flask API port | Integer | Yes |

```json
{
  "BROKER_HOST": "MQTT broker IP address",
  "BROKER_PORT": "MQTT broker port",
  "API_HOST": "Flask API IP address",
  "API_PORT": " Flask API port"
}
