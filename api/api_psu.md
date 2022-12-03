# API Power SUpply (PSU)

| Topic                       | QOS | Retain |
| :-------------------------- | :-: | :----: |
| {INTERFACE_PREFIX}/cmds/set |  0  | false  |
| {INTERFACE_PREFIX}/atts     |  0  |  true  |

**cmds/set** to change a configuration, the payload can be partial with only the element that need to change

**atts** to read the psu configuration, the payload **must** always be complete !

```json
    {
        "state": {
            "value": "on"
        },
        "volts": {
            "value": 3.3,
            "min":  0,
            "max": 50,
            "scale": 0.01
        },
        "current": {
            "value": 0.1,
            "min":  0,
            "max": 50,
            "scale": 0.01
        },
        "settings": {
            "ovp": true,
            "silent": false,
        }
    }
```

