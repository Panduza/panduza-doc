---
title: "Perf"
weight: 300
---

This document describes the specific attributes of Perf interfaces.

Please refer to [API interface](/docs/mqtt/core.md) to get a generic description of the interface mechanism.

The goal of the perf interface is to provide a way to test performance of the chain client/network/broker/platform.

## Info

```json
{
    "type": "perf",
    "version": "0.0.0"
}
```

### Changelog

#### Version 0.0

- Experimentations

## Attributes

| Attribute name | Retain Topic |
| :------------: | :----------: |
|    ping        |     True     |

### `[PLATF_00000_00]` - Attribute 'ping'

This attribute **must** have the following fields:

| Field name |            Description             | Default | Type  | Read-only |
| :--------- | :--------------------------------: | :-----: | :---: | :-------: |
| value      | Contains the value set by the user |    0    | bytes |   False   |

This attribute just set back the value.
