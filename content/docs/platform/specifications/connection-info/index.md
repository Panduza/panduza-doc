---
title: "Connection Info"
weight: 100
description: "The configuration file providing the broker host and credentials that must be used by the platform"
icon: cloud
---

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

| Field              | Description                        | Type    | Default     |
| ------------------ | ---------------------------------- | ------- | ----------- |
| `host/addr`        | MQTT broker IP address or hostname | String  | "localhost" |
| `host/port`        | MQTT broker port                   | Integer | 1883        |
| `credentials/user` | Username                           | String  | ""          |
| `credentials/pass` | Password                           | Strign  | ""          |

### `[CONF_REQ_FILE_NET_0030_00]` - Platform behavior when file badly formated

This file is important for the platform because it defines the parameters of the platform connection. Without this connection the platform is useless.

So the user **must** explicitly know if the connection is not configured as requested.

The platform must stop immediately and report an accurate error to the admin through the log file or console in the following cases:

- At platform boot, if the file is badly formated
- At platform boot, if the file has not a json content
- At platform boot, if the json object inside the file is badly formated
- At platform boot, if json fields are badly formated
- At platform boot, if there are json fields not indicated in this specification

### `[CONF_REQ_FILE_NET_0040_00]` - Platform behavior when missing fields

If the file is well formatted but some json field are missing, the platform **must** provide the default value for missing fields.

If the file does not exist, all fields are considered as missing, so the platform has to start with all the default connection parameters.
