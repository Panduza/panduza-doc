---
title: "Local Service Discovery"
weight: 1
---

# Local Service Discovery

This feature allow a client to easily discover machine that host a platform connected to the local network.

### `[PLATF_REQ_DNS_0000_00]` - Service Port

This service **must** use the port 53035.

### `[PLATF_REQ_DNS_0010_00]` - Request Payload

A client that try to discover platofrm on the network **must** broadcast a json payload with the following content:

```json
{
    "search": true
}
```

All other payloads must be ignored.

### `[PLATF_REQ_DNS_0020_00]` - Answer Payload

The platform **must** answer with the following content:

```json
{
    "name": "name_of_the_platform",
    "version": 1.0
}
```

- **name**: User defined name for the platform
- **version**: Version of the platform
