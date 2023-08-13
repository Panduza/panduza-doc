---
title: "DIO (Digital I/O)"
weight: 1
---

# DIO (Digital I/O)

This document describes the specific attributes and commands of the digital IO API.

Please refer to [API interface](api/api_interface.md) for a generic description of interface APIs.

## Versionning

## Info

```json
{
    "type": "psu",
    "version": "0.0"
}
```

### Changelog

#### Version 0.0

- Experimentations

## Attributes

| Attribute name |     Description      |
|:---------------|:--------------------:|
| direction      | Direction of the I/O |
| value          |   Value of the I/O   |

### Direction

| Field name    |    Description     |  Type   | Read-only | pollable |
|:--------------|:------------------:|:-------:|:---------:|:--------:|
| value         |   "in" or "out"    | String  |   False   |          |
| pull          | "up"/"down"/"open" | String  |   False   |          |
| polling_cycle |                    | Integer |   False   |    NA    |

### State

| Field name    |       Description        |  Type   | Read-only | pollable |
|:--------------|:------------------------:|:-------:|:---------:|:--------:|
| active        |        true/false        | Boolean |   False   |          |
| active_low    | true/false default false | Boolean |   False   |          |
| polling_cycle |                          | Integer |   False   |    NA    |

## Examples

### Atts for value

`<interface>/atts/value`

```json
{
    "state" : {
        "active" : false
    }
}
```

### Commands

`<interface>/cmds/set`

```json
{
    "direction": "out",
    "state" : 1,
}
```
