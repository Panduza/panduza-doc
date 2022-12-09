# I/O API

This document describes the specific attributes and commands of the IO API.

Please refer to [API interface](api_interface.md) for a generic descipriton of interface APIs.

## Attributes

| Attribute name |     Description      |
| :------------- | :------------------: |
| direction      | Direction of the I/O |
| value          |   Value of the I/O   |

### Direction

| Field name |  Description  |  Type  | Read-only |
| :--------- | :-----------: | :----: | :-------: |
| value      | "in" or "out" | String |   False   |

### Value

| Field name |     Description     |  Type   | Read-only |
| :--------- | :-----------------: | :-----: | :-------: |
| value      | 0 (low) or 1 (high) | Integer |   False   |

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
