---
title: "Serial"
weight: 3
---

A serial interface can be used to interact with any point to point serial communication adapter.

Examples:

- UART Adapter
- RS232 Adapter

This document describes the specific attributes of Serial interfaces.

Please refer to [API interface](../core.md) to get a generic description of the interface mechanism.

### `[PLATF_00012_00]` - Info

```json
{
    "type": "serial",
    "version": "0.0.0"
}
```

## Attributes

| Attribute name | Retain Topic |
| :------------- | :----------: |
| Tx             |    false     |
| Rx             |    false     |

### `[PLATF_00013_00]` - Serial Tx

Bytes Stream

### `[PLATF_00014_00]` - Serial Rx

Bytes Stream

## Changelog

### Version 0.0

- Experimentations


