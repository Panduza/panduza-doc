# MODBUS CLIENT API

This document describes the specific attributes and commands of the Modbus Client API.

Please refer to [API interface](api_interface.md) for a generic description of interface APIs.

**"type": "modbus.client"**

## Attributes

| Attribute name |                     Description                     |
| :------------- | :-------------------------------------------------: |
| coils          |                                                     |
| out_coils      |                    Output Coils                     |
| discret_in     |                   Discrete Inputs                   |
| input_regs     |                   Input Registers                   |
| holding_regs   |                  Holding Registers                  |
| watchlist      | Contains the configuration of the watched registers |


### Holding Registers (holding_regs)

| Field name |                     Description                     | Type | Read-only |
| :--------- | :-------------------------------------------------: | :--: | :-------: |
| values     |       Contains value of the watched registers       | json |   True    |

```json
"holding_regs": {
    "values": {
        "0": 350,
        "1": 450
    }
}
```

### Watchlist

| Field name | Description | Type | Read-only |
| :--------- | :---------: | :--: | :-------: |
| configs    |             | json |   True    |

```json
"watchlist": {
    "configs": [
        { "type": "holding_regs", "address": 0, "size": 10, "polling_time_s": 2.5 }
    ]
}
```

## Examples


### Command: To write a holding register

`<interface>/cmds/set`

To write the register 12 with value 42

```json
"holding_regs": {
    "values": [
        { "12": 42 }
    ]
}
```
