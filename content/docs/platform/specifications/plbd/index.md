---
title: "Panduza Local Broker Discovery (PLBD)"
description: "Service to help users to forget about IPs addresses in the local network"
icon: wifi_find
weight: 100
---

This feature allow a client to easily discover brokers on the local network that are used for panduza purpose.

## Requirements

### `[PLATF_00007_00]` - Service Port

This service **must** use the port 53035.

### `[PLATF_00008_00]` - Request Payload

A client that try to discover platofrm on the network **must** broadcast a json payload with the following *UTF-8* content:

```json
{
    "search": true
}
```

All other payloads must be ignored and platform must continue working.

### `[PLATF_00009_00]` - Answer Payload

The platform **must** answer with the following *UTF-8* content:

```json
{
    "platform": {
        "name": "name_of_the_platform",
        "version": 1.0,
    },
    "broker": {
        "addr": "192.168.1.1",
        "port": 1883
    }
}
```

- **platform/name**: User defined name for the platform that is responding
- **platform/version**: Version of the platform
- **broker/addr**: address of the broker
- **broker/port**: port of the broker

### `[PLATF_00010_00]` - Disable feature manually

The platform **must** provides a way to disable the PLBD feature through the **connection.json** file.

### `[PLATF_00011_00]` - Disable feature when connect to external IP

The platform **must** disable the PLBD feature when the broker is not on local network

## State of discussion

- **Why append this feature? Do we need it?**: Yes, some users are not confortable with IP address and sometimes it is boring event for advans users.
- **This service is a security issue**: No, a feature to find the platform is not a security issue if the broker is protected.
- **There must be a way to disable this feature from platform configuration**: Yes

