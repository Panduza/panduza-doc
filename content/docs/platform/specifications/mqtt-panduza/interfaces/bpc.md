---
title: "BPC (Bench Power Channel)"
weight: 2
---

# BPC (Bench Power Channel)

This document describes the specific attributes of Bench Power Channel interfaces.

Please refer to [API interface](/docs/mqtt/core.md) to get a generic description of the interface mechanism.

## Info

```json
{
    "type": "bpc",
    "version": "0.1.0"
}
```

## Attributes

| Attribute name | Retain Topic |
| :------------- | :----------: |
| enable         |     true     |
| voltage        |     true     |
| current        |     true     |

### >> Enable <<

Manage the state of the power supply output

| Field name    |       Description        | Default |  Type   | Read-only | pollable |
| :------------ | :----------------------: | :-----: | :-----: | :-------: | :------: |
| value         | True="on" or False="off" |  False  | Boolean |   False   |   True   |
| polling_cycle | TODEPRECATE              |         | Integer |   False   |    NA    |

### >> Voltage <<

Manage the voltage part of the power supply

| Field name    |                  Description                   |  Type   | Read-only | pollable |
| :------------ | :--------------------------------------------: | :-----: | :-------: | :------: |
| value         |       currently configured voltage value       |  Float  |   False   |   True   |
| min           |        minimal voltage value supported         |  Float  |   True    |  False   |
| max           |        maximal voltage value supported         |  Float  |   True    |  False   |
| decimals      | number of decimals supported for voltage value | Integer |   True    |  False   |
| polling_cycle | TODEPRECATE                                    | Integer |   False   |    NA    |

### >> Current <<

Manage the current part of the power supply

| Field name    |                   Description                   |  Type   | Read-only | pollable |
| :------------ | :---------------------------------------------: | :-----: | :-------: | :------: |
| value         |       currently configured amperage value       |  Float  |   True    |   True   |
| min           |        minimal amperage value supported         |  Float  |   True    |  False   |
| max           |        maximal amperage value supported         |  Float  |   True    |  False   |
| decimals      | number of decimals supported for amperage value | Integer |   True    |  False   |
| polling_cycle | TODEPRECATE                                     | Integer |   False   |    NA    |

### Changelog

#### Version 0.1.0

- First release for this interface

#### Version 0.0.0

- Experimentations
