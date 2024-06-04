---
title: "Video Stream"
weight: 3
---

# Video Stream

This document describes the specific attributes of Video Stream interfaces.

Please refer to [API interface](/docs/mqtt/core.md) to get a generic description of the interface mechanism.

## Info

This info is a special one with the *number_of_devices*

```json
{
    "type": "video_stream",
    "version": "0.0.0"
}
```

## Attributes

| Attribute name | Retain Topic |
| :------------- | :----------: |
| protocol       |     true     |
| url            |     true     |
| credential     |     true     |

### >> protocol <<

| Field name | Description | Default |  Type  | Read-only | pollable |
| :--------- | :---------- | :-----: | :----: | :-------: | :------: |
| name       |             |   NA    | String |   True    |  False   |

### >> url <<

| Field name | Description | Default |  Type  | Read-only | pollable |
| :--------- | :---------- | :-----: | :----: | :-------: | :------: |
| hostname   |             |   NA    | String |   True    |  False   |
| port       |             |   NA    | String |   True    |  False   |

### >> credential <<

| Field name | Description | Default |  Type  | Read-only | pollable |
| :--------- | :---------- | :-----: | :----: | :-------: | :------: |
| username   |             |   NA    | String |   True    |  False   |
| password   |             |   NA    | String |   True    |  False   |


### Changelog

#### Version 0.0

- Experimentations


