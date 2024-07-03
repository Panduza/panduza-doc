---
title: "Digital Input"
weight: 3
description: "To monitor a binary signal"
icon: "settings_input_component"
---

This document describes the specific attributes of digital input interfaces.

Please refer to [API interface](../core.md) to get a generic description of the interface mechanism.

### `[PLATF_00022_00]` - Info

```json
{
    "type": "digital_input",
    "version": 0
}
```

## Attributes

| Name    | Type |
| :------ | :--: |
| value   |  A1  |
| command |  A1  |

### `[PLATF_00023_00]` - value

- 1 for value [0 or 1]
- 1 for their last reading millisecond timestamps (0 if never read)

```json
{
    "value": 0,
    "timestamp_ms": 11111111111
}
```

### `[PLATF_00024_00]` - command

| Field name |                                 Description                                 |
| :--------- | :-------------------------------------------------------------------------: |
| frequency  | acquisition frequency (HZ) -> 0: immediate read, any value periodic reading |

## Changelog

### Version 0

- First Experimentations


