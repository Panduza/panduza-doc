---
title: "BLC (Bench Laser Control)"
weight: 2
---

# Laser

This document describes the specific attributes of Laser interfaces.

Please refer to [API interface](/docs/mqtt/core.md) to get a generic description of the interface mechanism.

## Info

```json
{
    "type": "blc",
    "version": "0.0.0"
}
```

## Attributes

| Attribute name | Retain Topic |
| :------------- | :----------: |
| mode           |     true     |
| enable         |     true     |
| power          |     true     |
| current        |     true     |

### >> Mode <<

This attribute is an enum, only one filed must be active at a time.

| Field name       | Description                            | Default |  Type   | Read-only |
| :--------------- | :------------------------------------- | :-----: | :-----: | :-------: |
| value            | Get/Set laser regulation mode          |  "constant_power"   | String Enum  |   False   |

Enum Values: 

- constant_power
- constant_current

### >> Enable <<

Manage the state of the interface

| Field name    |       Description        | Default |  Type   | Read-only | pollable |
| :------------ | :----------------------: | :-----: | :-----: | :-------: | :------: |
| value         | True="on" or False="off" |  False  | Boolean |   False   |   True   |

### >> Power <<

| Field name    |                  Description                   |  Type   | Read-only | pollable |
| :------------ | :--------------------------------------------: | :-----: | :-------: | :------: |
| value         |       currently configured voltage value       |  Float  |   False   |   True   |
| min           |        minimal voltage value supported         |  Float  |   True    |  False   |
| max           |        maximal voltage value supported         |  Float  |   True    |  False   |
| decimals      | number of decimals supported for voltage value | Integer |   True    |  False   |

### >> Current <<

| Field name    |                   Description                   |  Type   | Read-only | pollable |
| :------------ | :---------------------------------------------: | :-----: | :-------: | :------: |
| value         |       currently configured amperage value       |  Float  |   True    |   True   |
| min           |        minimal amperage value supported         |  Float  |   True    |  False   |
| max           |        maximal amperage value supported         |  Float  |   True    |  False   |
| decimals      | number of decimals supported for amperage value | Integer |   True    |  False   |

### Changelog

#### Version 0.0.0

- Experimentations

