---
title: "DIO (Digital I/O)"
weight: 1
---

# DIO (Digital I/O)

This document describes the specific attributes of Digital I/O interfaces.

Please refer to [API interface](/docs/mqtt/core.md) to get a generic description of the interface mechanism.

## Info

```json
{
    "type": "dio",
    "version": "0.0"
}
```

## Changelog

#### Version 0.0

- Experimentations

## Attributes

### Direction

This is the direction of the I/O. It must be configured before using th states

| Field name    |    Description                     |  Type   | Read-only | pollable |
|:--------------|:----------------------------------:|:-------:|:---------:|:--------:|
| value         |   "in" or "out"                    | String  |   False   |          |
| mode          | I/O Gate mode, depend on the value | String  |   False   |          |
| polling_cycle |                                    | Integer |   False   |    NA    |

#### Modes

*Output*

- "push-pull": a transistor connects to high, and a transistor connects to low (only one is operated at a time)
- "open-drain": a transistor connects to low and nothing else

*Input*

- "pull-up": a resistor connected to high
- "pull-down": a resistor connected to low


### State

| Field name    |       Description        |  Type   | Read-only | pollable |
|:--------------|:------------------------:|:-------:|:---------:|:--------:|
| active        |        true/false        | Boolean |   False   |          |
| active_low    | true/false default false | Boolean |   False   |          |
| polling_cycle |                          | Integer |   False   |    NA    |


