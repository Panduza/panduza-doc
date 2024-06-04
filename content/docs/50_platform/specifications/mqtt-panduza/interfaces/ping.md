---
title: "Ping"
weight: 300
---

This document describes the specific attributes of Ping interfaces.

Please refer to [API interface](/docs/mqtt/core.md) to get a generic description of the interface mechanism.

The goal of the ping interface is to provide a way to test performance of the chain client/network/broker/platform.

## Info

```json
{
    "type": "ping",
    "version": "0.0.0"
}
```

### Changelog

#### Version 0.0

- Experimentations

## Attributes

| Attribute name | Retain Topic |
| :------------: | :----------: |
|    mirror      |     True     |

### `[PLATF_00000_00]` - Attribute 'mirror'

This attribute **must** have the following fields:

| Field name |            Description             | Default | Type  | Read-only |
| :--------- | :--------------------------------: | :-----: | :---: | :-------: |
| value      | Contains the value set by the user |    0    | bytes |   False   |

This attribute just set back the value allowing the client to perform a spee check.
