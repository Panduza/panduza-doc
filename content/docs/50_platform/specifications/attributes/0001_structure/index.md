---
title: "Structure"
description: ""
weight: 0001
icon: grid_view
---




Readonly

```json
{
    "_": {
        "_": {
            "structure": {
                "type": "json"
            }
        }
    },
    "device_1": {
        "interface_1": {
            "interface_n": {
                "att_1": {
                    "type": "foo",
                    "constants": {  }
                },
                "att_n": {
                    "type": "foo"
                }
            }
        }
    }
}
```

- first layer must be the device name
- a json object with a "type" fields declares a attribute layer
- other layers are interface layers
