---
title: "Connection Info"
weight: 100
description: "The configuration file providing the broker host and credentials that must be used by the platform"
icon: cloud
---

This file is `very important` for the platform because it defines the parameters of the platform connection. Without this connection the platform is useless.

### `[CONF_REQ_FILE_NET_0010_00]` - Name and location

The file name **must** be `connection.json`.

ITs location **must** be:

- **Linux** Path: `\etc\panduza\`
- **Windows** Path : `C:\Users\UF...\conf\` 

### `[CONF_REQ_FILE_NET_0020_00]` - Content of the configuration file

The file **must** be in *JSON* format.

The file **must** be structured as follow:

```json
{
  "host": {
    "addr": "localhost",
    "port": 18833,
  },
  "credentials": {
    "user": "foo",
    "pass": "xxxxxxxxxx"
  }
}
```

| Field              | Description                        | Type    | Default     | Mandatory |
| ------------------ | ---------------------------------- | ------- | ----------- | --------- |
| `host/addr`        | MQTT broker IP address or hostname | String  | "localhost" | True      |
| `host/port`        | MQTT broker port                   | Integer | 1883        | True      |
| `credentials/user` | Username                           | String  | ""          | False     |
| `credentials/pass` | Password                           | Strign  | ""          | False     |

### `[CONF_REQ_FILE_NET_0025_00]` - Log connection information at platform boot

When the platform boot, it **must** display the connection info used in logs.

### `[CONF_REQ_FILE_NET_0030_00]` - Platform behavior when file badly formated

The user **must** explicitly know if the connection is not configured as requested.

The platform must stop immediately and report an accurate error to the admin through the log file or console in the following cases:

- At platform boot, if the file is badly formated
- At platform boot, if the file has not a json content
- At platform boot, if the json object inside the file is badly formated
- At platform boot, if json fields are badly formated
- At platform boot, if there are json fields not indicated in this specification


### `[CONF_REQ_FILE_NET_0040_00]` - Platform behavior when missing fields

If the file exists and is well formatted but some json field are missing, the platform **must** provide the default value for *non-mandatory missing fields*.

The platform must stop immediately and report an accurate error to the admin through the logs for mandatory feilds.

### `[CONF_REQ_FILE_NET_0050_00]` - Platform behavior when file not found

If the file does not exist, all fields are considered as missing, so the platform **must** start with all the default connection parameters after asking to users through console if he is ok with this (usefull for users that are discovering Panduza on Local Broker).

```
"No configuration file found. Do you want to create one with default settings?" [N/y]
```

We don't want a user starts the platform on default settings thinking he is starting its own.
