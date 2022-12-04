# API SPI

| Topic                       | QOS | Retain |
| :-------------------------- | :-: | :----: |
| {INTERFACE_PREFIX}/cmds/set |  0  | false  |
| {INTERFACE_PREFIX}/atts     |  0  |  true  |

This api has 2 state attributes:

- state
- custom_user
- settings

```json
{
    "state": {
        "value": "on"
    },
    "custom_user": {
        "TOTO": "on"
    },
    "settings": {
        "bitrate_hz": 4000000,
        "clock_polarity": 0,            // CPOL 0 or 1
        "clock_phase": 0,               // CPHA 0 or 1
        "bitorder": "msb",              // msb/lsb
        "ss_polarity": "active_low"     // active_low / 
    }
}
```

| Topic                        | QOS | Retain |
| :--------------------------- | :-: | :----: |
| {INTERFACE_PREFIX}/cmds/send |  0  | false  |
| {INTERFACE_PREFIX}/atts/data |  0  |  true  |

**cmds/send** to send data

**atts/data** to read incoming data

This api has 1 stream attribute:

- data

```json
{
    "data": {
        "value": "ddkdkdkkkdkd"
    },
}
```

