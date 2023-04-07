# Tutorial to Control remote digital input output of a pico using panduza ecosystem

This documentation will explain the following steps that you will have to configure in order to control remotely 
pico IO using modbus protocol and MQTT witch is a protocol to publish and subscribe data

To reach this goal, you will have to configure the PICO micro-controler, install the panduza eco-system and configure a client 
to send data to the panduza platform. The panduza plateform will manage the connexion between the PICO and the panduza eco-system.


Like you have seen bellow, there are various step to do before actually control I/O of the PICO
The first step will be to configure the PICO correctly.

But before, let's otherview what is the modbus protocol and the recommended configuration you will need to dispose.

# Modbus protocol

The modbus protocol is a way to exchange communication between various electronic and industrial equipments. It is often used in industrial projects. Therethore, we think it will be interesting to remote io interfaces of a microcontroler using modbus protocol.

Modbus protocole has his own bank register mapping. Each register has there own specifications

## Modbus register mapping

| Register                | access       | size (bits)| adress space |
|-------------------------|--------------|------------|--------------|
| coils register          | R/W          |   1        |00001 - 09999 |
| Discrete input          |  R           |    1       |10001 - 19999 |
| Input register          | R            |16          |30001 - 39999 |
| holding register        | R/W          |16          |40001 - 49999 |


For are purpose, we will manly be using coils and holdings register, because they have a read and write access.
The two other registers can be used to get specify data of the PICO such as the serial number of the number of IO of the pico.

There are two ways to communicate using modbus
TCP/IP mode => ethernet
RTU mode => serial

For this purpose, we will be using RTU mode.

To send data threw RTU mode, we have to send the following frame.


## RTU frame

|Start    |Slave ID | function code| data    | CRC    | Stop      |
|---------|---------|--------------|---------|--------|-----------|
|3.5 bytes|1 byte   |1 byte        | n bytes | 2 bytes| 3.5 bytes |


To send data, we will be using the pymodbus library. The user will only have to enter the data. The library thanks to there functions will create the frame and send them to the PICO.

In the PICO, we have included a specific library that will reconize the frame caracteristics, and it will parse the frame.

## Function codes pyModbus

If you want more information, and for debugging purposes, you can see the different function codes of the modbus protocol


|function code |Operation |
|---------     |--------- |
|  0x01   |      Read coils         |                  
|   0x02  |     Read discreate inputs          |                  
|   0x03  |      Read holding registers         |                   
|   0x04  |      Read Input registers         |                   
|   0x05  |      Write single coil         |                   
|   0x06  |      write single register         |                   
|   0x0F  |      write multiple coils         |                   
|    0x10 |      write multiple registers         |                   


# Configuration needed

For the configuration, it is recommended to use a Linux environment.

Make sure you have installed the following packages : 

```bash
  sudo apt install python3-pip # will install pip3 package
  sudo pip3 install pymodbus # will install python modbus library
  sudo pip3 install pyserial # will install python serial library
  sudo apt install cmake # will install cmake. Needed to build pico binaries
```

The panduza ecosystem will be installed when the client need's to be configured


# Configuration of the firmware to receive modbus data

The first step will be the configuration of the PICO so that it can receive data in modbus protocol

The firmware uses a library call liblightmodbus.

Ligthmodbus is a way to integrate modbus fonctionnalities in a embedded platform. The powerfull library allow's us to
configure platforms as master or slaves. In our example, the pico will be the slave.
But the most important is that the library is able to reconize and parse modbus RTU frame. Thanks to that, the firmware will no longer
have to check what type of frame is received.

A first version of the firmware has already been developped by our panduza developpers team.

in a directory clone the following repository :

```bash
  git clone git@github.com:Panduza/panduza-adapters-sdk.git # ssh key needed
```
The repository has various branches.
You need to checkout the following branch :

```bash
  git checkout addDIOtest
```

## how to build the project

in the root of the directory you will have to do to the following directory : 

```bash
  cd examples/pza-pico-modbus-dio
```

Once you are in this directory you can do the following steps to build the project

### Make sure cmake is installed ! 
```bash
  cmake --version
```

### How to build
```bash 
  mkdir build && cd build && cmake .. && make # this may take some time.
```
the following command will generate binary files.
In order to program the PICO, you will have to drop the .uf2 file to the pico.

In order to do this, you need to check the following requirements : 
the PICO is in boot mode.

to make sure type lsusb command in linux terminal and you should see the following line : 

```bash
  Bus 001 Device 018: ID 2e8a:0003 Raspberry Pi RP2 Boot
```



## use the following yml file :

```yml
  # docker compose run --service-ports mosquitto
  mosquitto:
    image: eclipse-mosquitto
    ports:
      - 1883:1883
      - 9001:9001
    volumes:
      - ./data/mosquitto.conf:/mosquitto/config/mosquitto.conf


  panduza-py-platform:
    # image: ghcr.io/panduza/panduza-py-platform:latest
    # To use your local platform build
    image: local/panduza-py-platform
    privileged: true
    depends_on:
      - mosquitto
    network_mode: host
    volumes:
      - .:/etc/panduza
      - /run/udev:/run/udev:ro
    # command: bash
```

## use the following json file :

```json
{
    "machine": "my_lab_server",
    "brokers": {
        "test_broker": {
            "addr": "localhost",
            "port": 1883,
            "interfaces": [
                {
                    "name": "My_Input_Output",
                    "driver": "pza_modbus_dio",
                    "settings":{
                        "port":"/dev/ttyACM0"
                    }
                }
            ]
        }
    }
}

```

## Build image

```bash
docker build --no-cache --tag local/panduza-py-platform:latest . 

```
## Run docker compose

```bash
docker compose up
```
## use the following script to test communication with MQTT broker
```bash
# Import
import time 
import argparse
from panduza import Client, Dio, Psu

# CONFIGURATION
BROKER_ADDR="localhost"
BROKER_PORT=1883
CHECK_USER_INPUT=True
RUN_TEST=False
TOPIC="pza/paul_lab/pico/dio"

testClient = Client(url=BROKER_ADDR, port=1883)
testClient.connect()
testClient.scan_interfaces()

d = Dio(addr=BROKER_ADDR, port=BROKER_PORT, topic=TOPIC)

for topic in inter:
  print(f"- {topic} => {inter[topic]['type']}")

d = Dio(addr=BROKER_ADDR, port=BROKER_PORT, topic=TOPIC, client=testClient)


d.direction.value.set("out", ensure = False)
d.direction.pull.set("open", ensure = False)
d.direction.polling_cycle.set(15, ensure = False)

d.state.active.set(False, ensure = False)
d.state.active_low.set(False, ensure = False)
d.state.polling_cycle.set(1, ensure = False)

```

## in topic 
```bash
pza/my_lab_server/pza_modbus_dio/My_Input_Output
```

### you must see the following json file

```json
{
  "direction":{
    "value":"in",
    "pull": "down", 
    "polling_cycle":5
    },
    "state":{
      "active":True,
      "active_low":True,
      "polling_cycle":5
    }  
}
```


