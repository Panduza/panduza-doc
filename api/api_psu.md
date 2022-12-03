# API Power SUpply (PSU)

## State management

| Topic                             | QOS | Retain |
| :-------------------------------- | :-: | :----: |
| {INTERFACE_PREFIX}/cmds/state/set |  0  | false  |
| {INTERFACE_PREFIX}/atts/state     |  0  |  true  |

### Payload

```json
    {
        "value": "off"
    }
```

|  Key  |  Type  |  Description  |
| :---: | :----: | :-----------: |
| value | string | "on" or "off" |

## Voltage management

| Topic                             | QOS | Retain |
| :-------------------------------- | :-: | :----: |
| {INTERFACE_PREFIX}/cmds/volts/set |  0  | false  |
| {INTERFACE_PREFIX}/atts/volts     |  0  |  true  |


### Payload

```json
    {
        "value": 5,
        "min":  0,
        "max": 50,
        "scale": 0.01
    }
```

|  Key  |  Type  |                 Description                 |
| :---: | :----: | :-----------------------------------------: |
| value | number |   volts value to set on the power supply    |
|  min  | number | mininal value that the power supply can set |
|  max  | number | maximal value that the power supply can set |
| scale | number |             decimal precision            |

To set the value the user is not forced to put min, max and scale into the payload. He can just send a payload with value.

## Current management

