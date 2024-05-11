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

### `[PLATF_REQ_ITF_PLATFORM_0010_00]` - Info 'number_of_devices' field

Info attribute of the platform interface **must** have a special field 'number_of_devices'.
This field contains the total number of devices mounted by the platform.

### `[PLATF_REQ_ITF_PLATFORM_0020_00]` - Info 'dying_gasp' field

Info attribute of the platform interface **must** have a special field 'dying_gasp'.
This field must be set to *true* on the last info message sent before the platform stop working else it must always be set to *false*

### Changelog

#### Version 0.0

- Experimentations

## Attributes

| Attribute name | Retain Topic |
| :------------: | :----------: |
|    control     |     True     |
|     dtree      |     True     |
|    devices     |     True     |


### `[PLATF_REQ_ITF_PLATFORM_0100_00]` - Attribute 'control'

Running configuration of the platform described with a device tree

This attribute **must** have the following fields:

| Field name |                        Description                        | Default | Type | Read-only |
| :--------- | :-------------------------------------------------------: | :-----: | :--: | :-------: |
| running    | Always true, set it to false to request the platform stop |  True   | bool |   False   |


### `[PLATF_REQ_ITF_PLATFORM_0110_00]` - Attribute 'dtree'

Running configuration of the platform described with a device tree

This attribute **must** have the following fields:

| Field name |                        Description                        | Default |  Type   | Read-only |
| :--------- | :-------------------------------------------------------: | :-----: | :-----: | :-------: |
| name       |             name of the active configuration              |         | string  |   False   |
| saved      | true if the content is the same as the active config file |         | boolean |   False   |
| list       |                 list of all configuration                 |         |  list   |   True    |
| content    |                current tree configuration                 |         |  json   |   False   |

### `[PLATF_REQ_ITF_PLATFORM_0120_00]` - Attribute 'devices'

To get information about the capabilites of the platform (device supported and connected to the server)

This attribute **must** have the following fields:

| Field name |                         Description                          | Default |  Type   | Read-only |
| :--------- | :----------------------------------------------------------: | :-----: | :-----: | :-------: |
| hunting    |     true if the platform is currently scannnig its ports     |  False  | boolean |   False   |
| max        |                 number of device registered                  |         |   int   |   True    |
| hunted     |                   number of device scanned                   |         |   int   |   True    |
| store      | available devices in the platform (including hunt detection) |         |  json   |   True    |


Store structure

```json
{
    "manu.model (device ref)": {
        "settings_props': { },
        "instances': [ ]
    }
}
```

### `[PLATF_REQ_ITF_PLATFORM_0120_00]` - Attribute 'ping'

The goal of the ping attribute is to provide a way to test performance of the chain client/network/broker/platform.

This attribute **must** have the following fields:

| Field name |                         Description                          | Default |  Type   | Read-only |
| :--------- | :----------------------------------------------------------: | :-----: | :-----: | :-------: |
| value      |     Contains the value set by the user                       |  0      | integer |   False   |

When a client wants to start a perf test, he send 1 and wait for answer, then 2, then 3... the goal is to measure the number of iteration in 1 seconde.




