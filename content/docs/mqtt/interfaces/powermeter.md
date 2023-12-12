---
title: "Powermeter"
weight: 3
---

# Powermeter

This document describes the specific attributes of Powermeter interfaces.

Please refer to [API interface](/docs/mqtt/core.md) to get a generic description of the interface mechanism.

## Info

```json
{
    "type": "powermeter",
    "version": "0.0.0"
}
```

## Attributes

| Attribute name | Retain Topic |
| :------------- | :----------: |
| measure        |     true     |

### >> Measure <<

Manage the state of the power supply output

| Field name |              Description               | Default |  Type   | Read-only |
| :--------- | :------------------------------------: | :-----: | :-----: | :-------: |
| value      |          value of the measure          |   NA    |  Float  |   True    |
| decimals   | number of decimals supported for value |   NA    | Integer |   True    |
| afrq       |       acquisition frequency (HZ)       |         |  Float  |   False   |

### Changelog

#### Version 0.0

- Experimentations


