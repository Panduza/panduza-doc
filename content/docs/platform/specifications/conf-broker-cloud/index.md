---
title: "network.json"
weight: 100
description: "The configuration file of the cloud mosquitto broker"
icon: network
---
## Specification of the `network.json` configuration file

### `[CONF_REQ_FILE_NET_0010_00]` - Location and format of the configuration file
**Windows** Path : `C:\Users\UF...\conf\` 

**Linux** Path: `\etc\panduza\` 

The `network.json` configuration file must be in **JSON** format.

### `[CONF_REQ_FILE_NET_0020_00]` - Content of the configuration file
The `network.json` configuration file must contain the following information:

| Field | Description | Type | Required |
| --- | --- | --- | --- |
| `broker_host` | MQTT broker IP address | String | Yes |
| `broker_port` | MQTT broker port | Integer | Yes |


```json
{
  "broker_host": "MQTT broker IP address",
  "broker_port": "MQTT broker port",
}
