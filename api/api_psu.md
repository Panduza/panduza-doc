# Power Supply Unit (PSU) API

This document describes the specific attributes and commands of the Power Supply Unit API.

Please refer to [API interface](api/api_interface.md) for a generic description of interface APIs.

## Attributes

| Attribute name |    Description    | Retain Topic  |
| :------------- | :---------------: | :-----------: |
| state          | State (on or off) | true          |
| volts          |      Voltage      | true          |
| amps           |     Amperage      | true          |
| settings       |     Settings      | true          |

### State

| Field name |  Description  |  Type  | Read-only |
| :--------- | :-----------: | :----: | :-------: |
| value      | "on" or "off" | String |   False   |

### Volts

Each value is represented in volts.

| Field name |                  Description                   |  Type   | Read-only |
| :--------- | :--------------------------------------------: | :-----: | :-------: |
| real       |             current voltage value              |  Float  |   True    |
| goal       |               voltage goal value               |  Float  |   False   |
| min        |         minimal voltage goal supported         |  Float  |   True    |
| max        |         maximal voltage goal supported         |  Float  |   True    |
| decimals   | number of decimals supported for voltage value | Integer |   True    |

### Amps

Each value is represented in amperes.

| Field name |                   Description                   |  Type   | Read-only |
| :--------- | :---------------------------------------------: | :-----: | :-------: |
| real       |             current amperage value              |  Float  |   True    |
| goal       |               amperage goal value               |  Float  |   False   |
| min        |         minimal amperage goal supported         |  Float  |   True    |
| max        |         maximal amperage goal supported         |  Float  |   True    |
| decimals   | number of decimals supported for amperage value | Integer |   True    |

### Settings

| Field name |       Description       |  Type   | Read-only |
| :--------- | :---------------------: | :-----: | :-------: |
| ovp        | Over Voltage Protection | Boolean |   False   |
| ocp        | Over Current Protection | Boolean |   False   |
| silent     |       Silent mode       | Boolean |   False   |

### Misc

| Field name   |   Description    |    Type     | Read-only |
| :----------- | :--------------: | :---------: | :-------: |
| serial_port  |   Serial port    |   String    |   True    |
| polling_time | Polling time (1) | JSON object |     -     |

(1) When a power supply setting is changed manually, it may not be able to notify the driver.
Therefore, the driver has to poll information.

The JSON object of polling_time is as described:

Each value is represented in milliseconds.

| Field name |                      Description                      |  Type   | Read-only |
| :--------- | :---------------------------------------------------: | :-----: | :-------: |
| value      |                    refresh period                     | Integer |   False   |
| min        | shortest refresh period supported<br>(0 == unlimited) | Integer |   True    |
| max        | longest refresh period supported<br>(0 == unlimited)  | Integer |   True    |

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
