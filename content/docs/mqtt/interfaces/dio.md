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

## Attributes

| Attribute name | Retain Topic |
| :------------- | :----------: |
| direction      |     True     |
| state          |     True     |

### >> Direction <<

This is the direction of the I/O. It must be configured before using th states

| Field name    |            Description             |   Default   | Type  | Read-only | pollable |
| :------------ | :--------------------------------: | :---------: | :---: | :-------: | :------: |
| value         |           "in" or "out"            |    "in"     | False |           |          |
| mode          | I/O Gate mode, depend on the value | "pull-down" | False |           |          |
| polling_cycle |                                    |             | False |    NA     |          |

#### Modes

when value is *out*

- "push-pull": a transistor connects to high, and a transistor connects to low (only one is operated at a time)
- "open-drain": a transistor connects to low and nothing else

when value is *in*

- "pull-up": a resistor connected to high
- "pull-down": a resistor connected to low

### >> State <<

This is the activation state of the I/O.

| Field name    |            Description            | Default |  Type   | Read-only | pollable |
| :------------ | :-------------------------------: | :-----: | :-----: | :-------: | :------: |
| active        |    Activation value of the I/O    |  False  | Boolean |   False   |          |
| active_low    | Reverse physical activation level |  False  | Boolean |   False   |          |
| polling_cycle |                                   |         | Integer |   False   |    NA    |

The `state` does not represent the HIGH/LOW information, it also depend of the `active_low`

| active | active_low | pin level |
| :----- | :--------: | :-------: |
| True   |    True    |   HIGH    |
| False  |   False    |    LOW    |
| True   |    True    |    LOW    |
| False  |   False    |   HIGH    |

## Changelog

#### Version 0.0

- Experimentations
