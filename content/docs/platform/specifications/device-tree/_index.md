---
title: "Device Tree"
weight: 2
bookCollapseSection: true
---

# Device Tree

The `tree.json` settings file exlpains to the platform which device that have te be managed and how.

`
The core philosophy of this file is to be very simple when you start by setting all the default choices for you, but the more you understand the file and need control over the platform the more you can get ! 
`

### `[PLATF_REQ_TREE_0000_00]` - Main file structure

The tree file **must** be json formated.

The root of the file **must** contain at least the following sections:

- devices
- benches
- brokers

```json
{
    "devices": [
        ...
    ],
    "benches": [
        ...
    ],
    "brokers": [
        ...
    ]
}
```

# Devices Section

This section allow users to define the device he wants to control.

### `[PLATF_REQ_TREE_0010_00]` - Devices Section Structure

Devices sections **must** be an array of device definition.

```json
{
    "devices": [
        { defintion_1 },
        { defintion_2 }
        ...
        { defintion_n }
    ],
}
```

## Device Definition

Device definition provides to the platform all the information required to instanciate the correct driver and configure it.

### `[PLATF_REQ_TREE_0100_00]` - Device Definition Structure

The device definition **must** contain at least the *model* field.

It **might** also contains 2 other fields: *name* and *settings*

```json
{
    "model": "model_example",
    "name": "name_example",
    "settings": { }
}
```

### `[PLATF_REQ_TREE_0110_00]` - Device Definition Model Field

### `[PLATF_REQ_TREE_0120_00]` - Device Definition Name Field

### `[PLATF_REQ_TREE_0130_00]` - Device Definition Settings Field


# Benches Section

This section allow users to group the device into bench.

### `[PLATF_REQ_TREE_0200_00]` - Benches Section Structure

Benches sections **must** be an array of bench definition.

```json
{
    "benches": [
        { defintion_1 },
        { defintion_2 }
        ...
        { defintion_n }
    ],
}
```

## Bench Definition


# Brokers Section

This section allow users to define the broker used for each bench or device.

### `[PLATF_REQ_TREE_0300_00]` - Brokers Section Structure

Brokers sections **must** be an array of broker definition.

```json
{
    "brokers": [
        { defintion_1 },
        { defintion_2 }
        ...
        { defintion_n }
    ],
}
```

## Broker Definition

Broker definition associate a broker to benches and devices.

```json
{
    "settings": { ... },
    "benches" : [ ... ],
    "devices" : [ ... ],
}
```

### `[PLATF_REQ_TREE_0310_00]` - Broker Definition Settings Field

```json
{
    "host": "localhost",
    "port": 1883,
}
```

### `[PLATF_REQ_TREE_0320_00]` - Broker Definition Benches Field

### `[PLATF_REQ_TREE_0330_00]` - Broker Definition Devices Field


