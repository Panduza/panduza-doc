# Power Supply Unit (PSU) API

This document describes the specific attributes and commands of the Power Supply Unit API.

Please refer to [API interface](api_interface.md) for a generic descipriton of interface APIs.

## Attributes

| Attribute name |    Description    |
| :------------- | :---------------: |
| state          | State (on or off) |
| volts          |      Voltage      |
| amps           |     Amperage      |
| settings       |     Settings      |

### State

| Field name |  Description  |  Type  | Read-only |
| :--------- | :-----------: | :----: | :-------: |
| state      | "on" or "off" | String |   False   |

### Volts

Each value is represented in volts unit.

| Field name |                  Description                   |  Type   | Read-only |
| :--------- | :--------------------------------------------: | :-----: | :-------: |
| value      |                 voltage value                  |  Float  |   False   |
| min        |        minimal voltage value supported         |  Float  |   True    |
| max        |        maximal voltage value supported         |  Float  |   True    |
| decimals   | number of decimals supported for voltage value | Integer |   True    |

### Amps

Each value is represented in amps unit.

| Field name |                   Description                   |  Type   | Read-only |
| :--------- | :---------------------------------------------: | :-----: | :-------: |
| value      |                 amperage value                  |  Float  |   False   |
| min        |        minimal amperage value supported         |  Float  |   True    |
| max        |        maximal amperage value supported         |  Float  |   True    |
| scale      | number of decimals supported for amperage value | Integer |   True    |

### Settings

| Field name |                   Description                   |  Type   | Read-only |
| :--------- | :---------------------------------------------: | :-----: | :-------: |
| serial_port      |                 Serial port                  |  String  |   False   |
| ovp        |        Over Voltage Protection         |  Boolean  |   False    |
| ocp        |        Over Current Protection        |  Boolean  |   False    |
| silent      | Silent mode | Boolean |   True    |
| refresh_period      | Refresh period in milliseconds (0 == disabled) | Integer |   False    |

## Examples

### Atts for volts

`<interface>/atts/volts`

```json
{
    "volts" : {
        "value" : 3.30,
        "min" : 0,
        "max" : 30,
        "scale" : 2
    }
}
```

### Commands

`<interface>/cmds/set`

```json
{
    "state" : "on",
    "volts": 3.3,
    "amps" : 0.5,
    "settings" : {
        "ovp" : true,
        "ocp" : true,
        "silent" : false,
        "refresh_period" : 0
    }
}
```