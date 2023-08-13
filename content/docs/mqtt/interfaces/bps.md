---
title: "BPS (Bench Power Supply)"
weight: 2
---

# BPS (Bench Power Supply)


This page describes the specific attributes and commands of the Power Supply Unit API.

Please refer to [API interface](api/api_interface.md) for a generic description of interface APIs.

## Versionning

## Info

```json
{
    "type": "psu",
    "version": "0.1"
}
```

### Changelog

#### Version 0.1

- Initial stable version
- 'state' attribute is renamed into 'enable'
- 'enable.value' field is retyped into 'boolean'
- 'polling_cycle' on attributes is added

#### Version 0.0

- Experimentations

## Attributes

This section provides attributes of the Power Supply Interface

| Attribute name |             Description              | Retain Topic |
|:---------------|:------------------------------------:|:------------:|
| enable         |      State of the power output       |     true     |
| volts          |          Voltage management          |     true     |
| amps           |         Amperage management          |     true     |
| settings       | Special Settings of the power supply |     true     |

### Enable

Manage the state of the power supply output

| Field name    |       Description        |  Type   | Read-only | pollable |
|:--------------|:------------------------:|:-------:|:---------:|:--------:|
| value         | True="on" or False="off" | Boolean |   False   |   True   |
| polling_cycle |                          | Integer |   False   |    NA    |

### Volts

Manage the voltage part of the power supply

| Field name    |                  Description                   |  Type   | Read-only | pollable |
|:--------------|:----------------------------------------------:|:-------:|:---------:|:--------:|
| real          |             current voltage value              |  Float  |   True    |   True   |
| goal          |               voltage goal value               |  Float  |   False   |   True   |
| min           |         minimal voltage goal supported         |  Float  |   True    |  false   |
| max           |         maximal voltage goal supported         |  Float  |   True    |  false   |
| decimals      | number of decimals supported for voltage value | Integer |   True    |  false   |
| polling_cycle |                                                | Integer |   False   |    NA    |

### Amps

Manage the current part of the power supply

| Field name    |                   Description                   |  Type   | Read-only | pollable |
|:--------------|:-----------------------------------------------:|:-------:|:---------:|:--------:|
| real          |             current amperage value              |  Float  |   True    |   True   |
| goal          |               amperage goal value               |  Float  |   False   |   True   |
| min           |         minimal amperage goal supported         |  Float  |   True    |  false   |
| max           |         maximal amperage goal supported         |  Float  |   True    |  false   |
| decimals      | number of decimals supported for amperage value | Integer |   True    |  false   |
| polling_cycle |                                                 | Integer |   False   |    NA    |

### Settings

Manage specific settings of the power supply (**!! unstable feature !!**)

| Field name    |       Description       |  Type   | Read-only | pollable |
|:--------------|:-----------------------:|:-------:|:---------:|:--------:|
| ovp           | Over Voltage Protection | Boolean |   False   |   True   |
| ocp           | Over Current Protection | Boolean |   False   |   True   |
| silent        |       Silent mode       | Boolean |   False   |   True   |
| polling_cycle |                         | Integer |   False   |    NA    |

## Examples

### Atts for volts

`<interface>/atts/volts`

```json
{
    "volts" : {
        "real" : 3.30,
        "goal" : 3.30,
        "min" : 0,
        "max" : 30,
        "decimals" : 2
    }
}
```

### Commands

`<interface>/cmds/set`

```json
{
    "enable" : true,
    "volts": 3.3,
    "amps" : 0.5,
    "settings" : {
        "ovp" : true,
        "ocp" : true,
        "silent" : false
    },
    "misc" : {
        "polling_cycle" : {
            "value" : 500 //milliseconds
        }
    }
}
```

