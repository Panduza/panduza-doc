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

This section allow to user to define the device he wants to control

### `[PLATF_REQ_TREE_0000_00]` - Main file structure


# Benches Section


# Brokers Section


