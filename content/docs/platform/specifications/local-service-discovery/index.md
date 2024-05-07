---
title: "Local Service Discovery"
description: "Service to help users to forget about IPs addresses"
icon: wifi_find
weight: 100
---

This feature allow a client to easily discover machine that host a platform connected to the local network.

## Requirements

### `[PLATF_REQ_LSD_0000_00]` - Service Port

This service **must** use the port 53035.

### `[PLATF_REQ_LSD_0010_00]` - Request Payload

A client that try to discover platofrm on the network **must** broadcast a json payload with the following *UTF-8* content:

```json
{
    "search": true
}
```

All other payloads must be ignored and platform must continue working.

### `[PLATF_REQ_LSD_0020_00]` - Answer Payload

The platform **must** answer with the following *UTF-8* content:

```json
{
    "name": "name_of_the_platform",
    "version": 1.0
}
```

- **name**: User defined name for the platform
- **version**: Version of the platform

### `[PLATF_REQ_LSD_0030_00]` - Disable feature

The platform **must** provides a way to disable the LSD feature.

`TODO`

## State of discussion

- **Why append this feature? Do we need it?**: Yes, some users are not confortable with IP address and sometimes it is boring event for advans users.
- **This service is a security issue**: No, a feature to find the platform is not a security issue if the broker is protected.
- **There must be a way to disable this feature from platform configuration**: Yes

