---
title: "Voltmeter"
weight: 3
---

# Voltmeter

This document describes the specific attributes of Voltmeter interfaces.

Please refer to [API interface](/docs/mqtt/core.md) to get a generic description of the interface mechanism.

## Info

```json
{
    "type": "voltmeter",
    "version": "0.0"
}
```

## Attributes

| Attribute name | Retain Topic |
| :------------- | :----------: |
| measure        |     true     |

### >> Measure <<

Manage the state of the power supply output

| Field name    |              Description               | Default |  Type   | Read-only | pollable |
| :------------ | :------------------------------------: | :-----: | :-----: | :-------: | :------: |
| value         |          value of the measure          |   NA    |  Float  |   True    |   True   |
| decimals      | number of decimals supported for value |   NA    | Integer |   True    |  False   |
| polling_cycle |                                        |         | Integer |   False   |    NA    |

### Changelog

#### Version 0.0

- Experimentations


