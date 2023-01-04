# Serial API

This document describes the specific attributes and commands of the serial API.

Please refer to [API interface](api_interface.md) for a generic description of interface APIs.

## Attributes

| Attribute name |    Description     |
| :------------- | :----------------: |
| data           | communication data |
| settings       |      Settings      |


### Data

| Field name |      Description      | Type  | Read-only |
| :--------- | :-------------------: | :---: | :-------: |
| tx         | Data you want to send | bytes |   False   |
| rx         |   Data you recieve    | bytes |   True    |


### Settings

| Field name  |         Description         |  Type  | Read-only |
| :---------- | :-------------------------: | :----: | :-------: |
| serial_port |   Host serial port found    | String |   True    |
| baudrate    | Baudrate of the serial port |  int   |   True    |

