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
    "number_of_devices": 0
}
```

### `[REQ_ITF_PLATFORM_0010_00]` - Info 'number_of_devices' field

Info attribute of the platform interface **must** have a special field 'number_of_devices'.
This field contains the total number of devices mounted by the platform.

### Changelog

#### Version 0.0

- Experimentations


