---
title: "Device"
weight: 3
---

# Device

This document describes the specific attributes of Device interfaces.

Please refer to [API interface](/docs/mqtt/core.md) to get a generic description of the interface mechanism.

## Info

This info is a special one with the *number_of_interfaces*

```json
{
    "type": "device",
    "version": "0.0.0",
    "number_of_interfaces": 0
}
```

### `[REQ_ITF_DEVICE_0010_00]` - Info 'number_of_interfaces' field

Info attribute of the device interface **must** have a special field 'number_of_interfaces'.
This field contains the total number of interfaces mounted by this device (this device interface included).

## Attributes

| Attribute name | Retain Topic |
| :------------- | :----------: |
| identity       |     true     |

### >> Identity <<

Manage the state of the power supply output

| Field name   | Description              | Default |  Type  | Read-only | pollable |
| :----------- | :----------------------- | :-----: | :----: | :-------: | :------: |
| family       | Device family name       |   NA    | String |   True    |  False   |
| model        | Device model name        |   NA    | String |   True    |  False   |
| manufacturer | Device Manufacturer name |   NA    | String |   True    |  False   |

### Changelog

#### Version 0.0

- Experimentations

