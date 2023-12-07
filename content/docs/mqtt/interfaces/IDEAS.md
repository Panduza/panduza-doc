
--- devices
PC/Server
Adatpeur uart

--- interfaces
RELP
  - AT over UART
  - SCPI over UART or ETH
  - SHELL over SSH

ByteStream
  -

--- connecteur ?
SerialPort
SSH



REPL and ByteStream does not manage config of ssh or serialport
Maybe too complex for nothing ?
Maybe it could ease the tests for SerialPort with RELP too (like SCPI or AT)
useless ? just do SSH & SerialPort + manage REPL or Stream in client ?

# REPL

L’acronyme Read-Eval-Print-Loop désigne une interface dans laquelle on peut écrire une commande, l’exécuter, voir s’afficher une réponse et recommencer.
En programmation on parle souvent console et dans l’utilisation d’un système unix de shell ou d’interface en ligne de commande CLI.


- command
  - UID (to be able to match async request)
  - command (text of the command)
  - answer (text of the answer)

- data_channel
  - command_layer (GENERIC/AT/SCPI/SHELL)
  - transport_layer (ssh/tcp_socket/udp_socket/serialport)
  - state (opened/closed)
  - 
  - **specific transport IP**
  - IP
  - port
  - credential => quid sur l'enregistrement des clefs SSH dans la platform ?
  -
  - **specific transport serial**
  - baudrate
  - parity
  - bitstop
  - ...

data_channel represents the underliyng layer of the REPL interface
Potentiel Use Case:
  - on commence les tests avec le shell serie d'un linux puis une fois la carte préte on continue avec le ssh.
  - un test qui lance des commandes peut passer par ssh ou lien serie sans changer
  - SCPI devient un REPL avec un data_channel (serialport ou TCP) par exemple

# ByteStream

- data
  - tx
  - rx
  
| Field name |      Description      |     Type      | Read-only |
| :--------- | :-------------------: | :-----------: | :-------: |
| tx         | Data you want to send | base64 string |   False   |
| rx         |   Data you recieve    | base64 string |   True    |


- channel
  - protocol (ssh/tcp_socket/udp_socket/serialport)
  - **else same as REPL channel**



-----------------------------------------------------


# Relay

# I2C

# SPI

# DIO

# AIO





-----------------------------------------------------

# ModbusClient


MODBUS CLIENT API

This document describes the specific attributes and commands of the Modbus Client API.

Please refer to [API interface](api_interface.md) for a generic description of interface APIs.

**"type": "modbus.client"**

## Attributes

| Attribute name |                     Description                     |
| :------------- | :-------------------------------------------------: |
| coils          |                                                     |
| out_coils      |                    Output Coils                     |
| discret_in     |                   Discrete Inputs                   |
| input_regs     |                   Input Registers                   |
| holding_regs   |                  Holding Registers                  |
| watchlist      | Contains the configuration of the watched registers |


Attribut en plus
- data_channel
  - transport_layer (TCP/RTU)
  - state (opened/closed)
  -
  - **specific modbus**
  - slave_id
  - 
  - **specific transport IP**
  - IP
  - port
  - credential => quid sur l'enregistrement des clefs SSH dans la platform ?
  -
  - **specific transport serial**
  - baudrate
  - parity
  - bitstop
  - ...


### Holding Registers (holding_regs)

| Field name |                     Description                     | Type | Read-only |
| :--------- | :-------------------------------------------------: | :--: | :-------: |
| values     |       Contains value of the watched registers       | json |   True    |

```json
"holding_regs": {
    "values": {
        "0": 350,
        "1": 450
    }
}
```

### Watchlist

| Field name | Description | Type | Read-only |
| :--------- | :---------: | :--: | :-------: |
| configs    |             | json |   True    |

```json
"watchlist": {
    "configs": [
        { "type": "holding_regs", "address": 0, "size": 10, "polling_time_s": 2.5 }
    ]
}
```

## Examples


### Command: To write a holding register

`<interface>/cmds/set`

To write the register 12 with value 42

```json
"holding_regs": {
    "values": [
        { "12": 42 }
    ]
}
```
