# DIO API

This document describes the specific attributes and commands of the digital IO API.

Please refer to [API interface](api/api_interface.md) for a generic description of interface APIs.

## Attributes

| Attribute name |     Description      |
| :------------- | :------------------: |
| direction      | Direction of the I/O |
| value          |   Value of the I/O   |

### Direction

| Field name   |  Description  |  Type   | Read-only | pollable |
|:-------------|:-------------:|:-------:|:---------:|:--------:|
| value        | "in" or "out" | String  |   False   |          |
| pull         | up/down/open  | String  |   False   |          |
| polling_time |               | Integer |   False   |    NA    |

### State

| Field name   |       Description        |  Type   | Read-only | pollable |
|:-------------|:------------------------:|:-------:|:---------:|:--------:|
| active       |        true/false        | Boolean |   False   |          |
| active_low   | true/false default false | Boolean |   False   |          |
| polling_time |                          | Integer |   False   |    NA    |

## Examples

### Atts for value

`<interface>/atts/value`

```json
{
    "value" : {
        "value" : 0
    }
}
```

### Commands

`<interface>/cmds/set`

```json
{
    "direction": "out",
    "value" : 1,
}
```
