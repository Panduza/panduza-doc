---
title: "Registers"
weight: 3
icon: "list_alt"
---

A registers interface allow the user to control a register map with write and read operations.

This document describes the specific attributes of registers interfaces.

Please refer to [API interface](../core.md) to get a generic description of the interface mechanism.

### `[PLATF_00015_00]` - Info

```json
{
    "type": "registers",
    "version": 0
}
```

## Commands

The command topic for this interface is as follow:

To write a register

```json
{
    "cmd": "w",
    "index": 0,
    "values": [42],
    "repeat": 500
}
```

To write a multiple continous registers

```json
{
    "cmd": "w",
    "index": 0,
    "values": [42, 1, 2, 3],
    "repeat": 500
}
```

Index is the index of the register in its map, user will probably use address.
In that case, convertion between index and address must be done with settings.base_address and settings.register_size

```
address(index) = base_address + (index x register_size)
index(address) = (address - base_address) / register_size
```

To read 3 register from index 0

```json
{
    "cmd": "r",
    "index": 0,
    "size": 3,
    "repeat": 500
}
```

- repeat allow to repeat the command every X milliseconds


```json
{
    "cmd": "stop",
    "index": 0,
    "size": 3,
}
```


## Attributes

| Name     | Type |
| :------- | :--: |
| map      |  A3  |
| settings |  A1  |
| commands |  A2  |

### `[PLATF_00016_00]` - map

This attribute contains a 2 json array:

- 1 for the register map values 
- 1 for their last reading millisecond timestamps (0 if never read)

```json
{
    "values": [1,2,3],
    "timestamps_ms": [0, 111111111, 0]
}
```

### `[PLATF_00017_00]` - settings

| Field name         |                Description                |
| :----------------- | :---------------------------------------: |
| base_address       |          Base address of the map          |
| register_size      | size of a unique register (8, 16, 32, 64) |
| number_of_register |         total number of register          |

```json
{
    "base_address": 0,
    "register_size": 8,
    "number_of_register": 10
}
```

## Changelog

### Version 0

- First Experimentations


