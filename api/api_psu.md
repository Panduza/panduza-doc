# Power Supply Unit (PSU) API

This document describes the specific attributes and commands of the Power Supply Unit API.

Please refer to [API interface](api/api_interface.md) for a generic description of interface APIs.

## Attributes

| Attribute name |     Description     | Retain Topic |
|:---------------|:-------------------:|:------------:|
| enable         | State of the output |     true     |
| volts          |       Voltage       |     true     |
| amps           |      Amperage       |     true     |
| settings       |      Settings       |     true     |

### Enable

Manage the state of the power supply output

| Field name   |                Description                 |  Type   | Read-only | pollable |
|:-------------|:------------------------------------------:|:-------:|:---------:|:--------:|
| value        |          True="on" or False="off"          | Boolean |   False   |   True   |
| polling_time | Polling time  in milliseconds (0=disabled) | Integer |   False   |    NA    |

### Volts

Each value is represented in volts.

| Field name   |                  Description                   |  Type   | Read-only | pollable |
|:-------------|:----------------------------------------------:|:-------:|:---------:|:--------:|
| real         |             current voltage value              |  Float  |   True    |   True   |
| goal         |               voltage goal value               |  Float  |   False   |   True   |
| min          |         minimal voltage goal supported         |  Float  |   True    |  false   |
| max          |         maximal voltage goal supported         |  Float  |   True    |  false   |
| decimals     | number of decimals supported for voltage value | Integer |   True    |  false   |
| polling_time |   Polling time  in milliseconds (0=disabled)   |  Integer|   False   |    NA    |

### Amps

Each value is represented in amperes.

| Field name   |                   Description                   |  Type   | Read-only | pollable |
|:-------------|:-----------------------------------------------:|:-------:|:---------:|:--------:|
| real         |             current amperage value              |  Float  |   True    |   True   |
| goal         |               amperage goal value               |  Float  |   False   |   True   |
| min          |         minimal amperage goal supported         |  Float  |   True    |  false   |
| max          |         maximal amperage goal supported         |  Float  |   True    |  false   |
| decimals     | number of decimals supported for amperage value | Integer |   True    |  false   |
| polling_time |   Polling time  in milliseconds (0=disabled)    | Integer |   False   |    NA    |

### Settings

| Field name   |                Description                 |  Type   | Read-only | pollable |
|:-------------|:------------------------------------------:|:-------:|:---------:|:--------:|
| ovp          |          Over Voltage Protection           | Boolean |   False   |   True   |
| ocp          |          Over Current Protection           | Boolean |   False   |   True   |
| silent       |                Silent mode                 | Boolean |   False   |   True   |
| polling_time | Polling time  in milliseconds (0=disabled) | Integer |   False   |    NA    |

### Misc

| Field name   |   Description    |    Type     | Read-only |
| :----------- | :--------------: | :---------: | :-------: |
| serial_port  |   Serial port    |   String    |   True    |


## Examples

### Atts for volts

`<interface>/atts/volts`

```json
{
    "volts" : {
        "value" : 3.30,
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
    "state" : "on",
    "volts": 3.3,
    "amps" : 0.5,
    "settings" : {
        "ovp" : true,
        "ocp" : true,
        "silent" : false
    },
    "misc" : {
        "polling_time" : {
            "value" : 500 //milliseconds
        }
    }
}
```
