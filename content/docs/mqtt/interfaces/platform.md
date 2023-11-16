---
title: "Platform"
weight: 3
---

# Platform

This document describes the specific attributes of Platform interfaces.

Please refer to [API interface](/docs/mqtt/core.md) to get a generic description of the interface mechanism.

This interfaces will be stored in 

- pza/server/\<hostname>/device
- pza/server/\<hostname>/platform_py

## Info

```json
{
    "type": "platform",
    "version": "0.0.0",
    "number_of_devices": 0,
    "dying_gasp": false
}
```

### `[REQ_ITF_PLATFORM_0010_00]` - Info 'number_of_devices' field

Info attribute of the platform interface **must** have a special field 'number_of_devices'.
This field contains the total number of devices mounted by the platform.

### `[REQ_ITF_PLATFORM_0020_00]` - Info 'dying_gasp' field

Info attribute of the platform interface **must** have a special field 'dying_gasp'.
This field must be set to *true* on the last info message sent before the platform stop working else it must always be set to *false*

### Changelog

#### Version 0.0

- Experimentations

## Attributes

| Attribute name | Retain Topic |
| :------------- | :----------: |
| configuration  |     True     |
| device         |     True     |

### >> dtree <<

Running configuration of the platform described with a device tree

| Field name |                        Description                        | Default |  Type   | Read-only | pollable |
| :--------- | :-------------------------------------------------------: | :-----: | :-----: | :-------: | :------: |
| name       |             name of the active configuration              |         | string  |           |          |
| saved      | true if the content is the same as the active config file |         | boolean |           |          |
| list       |                 list of all configuration                 |         |  list   |           |          |
| content    |                current tree configuration                 |         |  json   |           |          |

how to append / delete / configure a device ?  set the running/configuration  attribute ?
save / load ?

### >> devices <<

To get information about the capabilites of the platform (device supported and connected to the server)

| Field name |                         Description                          | Default |  Type   | Read-only | pollable |
| :--------- | :----------------------------------------------------------: | :-----: | :-----: | :-------: | :------: |
| hunting    |     true if the platform is currently scannnig its ports     |         | boolean |   true    |          |
| max        |                 number of device registered                  |         |   int   |   true    |          |
| hunted     |                   number of device scanned                   |         |   int   |   true    |          |
| store      | available devices in the platform (including hunt detection) |         |  json   |           |          |
