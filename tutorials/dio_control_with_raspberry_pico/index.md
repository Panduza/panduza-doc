# Digital I/O Control with Raspberry Pico

This tutorial explains, step by step, how to configure a Raspberry Pico and use Panduza to perform simple DIO control.

`!!! OK POINT FIX DOC AFTER ONLY !!!`

`TODO: Improve this picture, too small on half screen, add some verticality`
![](_media/description.png)


# Requirements

This tutorial has been tested on Ubuntu 22.04.

Make sure you have installed the following packages : 

```bash
  sudo apt install python3-pip # will install pip3 package
  sudo pip3 install pymodbus # will install python modbus library
  sudo pip3 install pyserial # will install python serial library
  sudo apt install cmake # will install cmake. Needed to build pico binaries
```

`TODO: j'ai pas compris`
The panduza ecosystem will be installed when the client need's to be configured


`TODO: j'ai pas compris`
pico IO using modbus protocol and mosquitto using MQTT witch is a protocol to publish and subscribe data using tcp/ip architecture.

To reach this goal, you will have to configure the PICO micro-controler, install the panduza eco-system and configure a client 
to send data to the panduza platform. The panduza plateform will manage the connexion between the PICO and the panduza eco-system.


Like you have seen bellow, there are various step to do before actually control I/O of the PICO
The first step will be to configure the PICO correctly.

But before, let's otherview what is the modbus protocol and the recommended configuration you will need to dispose.



`TODO: Remove sections about the modbus protocol, user that want to control io on pico does not care on this tutorial, or speak about modbus very very quickly here`

In this document, we will explain the role of each block of the panduza chain from the client to the PICO.

But first, let's look other of the modbus protocole.

# Modbus protocol

The modbus protocol is a way to exchange communication between various electronic and industrial equipments. It is often used in industrial projects. Therethore, we think it will be interesting to remote io interfaces of a microcontroler using modbus protocol.

Modbus protocole has his own bank register mapping. Each register has there own specifications

## Modbus register mapping

| Register                | access       | size (bits)| adress space |
|-------------------------|--------------|------------|--------------|
| coils register          | R/W          |    1       |00001 - 09999 |
| Discrete input          |  R           |    1       |10001 - 19999 |
| Input register          | R            |    16      |30001 - 39999 |
| holding register        | R/W          |    16      |40001 - 49999 |


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




# MQTT configuration

In this part, we will see the steps to install mosquitto MQTT broker.

For this project, the server configuration will be defined as : 

```bash
  BROKER_ADDR="localhost"
  BROKER_PORT=1883
  CHECK_USER_INPUT=True
  RUN_TEST=False
```
We will be connected in localhost and the port 1883 is the default port to use mqtt protocol.

## mosquitto installation

To use MQTT protocole, you will have to install the mosquitto server.

This installation will install the broker MQTT packages.

It is possible to use command lines to install the mosquitto server.

```bash
  sudo apt update # update the environment
  sudo apt install -y mosquitto # install the mosquitto package
```

To make sure mosquitto is installed, you run the command : 

```bash
  mosquitto --version
```
you should have the following output in the terminal


![](../../_media/mosquitto_version.png)

Then ensure, that the mosquitto package is loaded by using the following command. 

```bash
  sudo systemctl status mosquitto
```
![](../../_media/mosquitto_loaded.png)


## installation of MQTT explorer

`TODO: Oui mais il faut montrer comment ça marche et comment on voit que ça fonctionne (mets le à la fin du tuto en bonus)`

MQTT explorer is a practical graphical tool used to testing communication via MQTT broker. With this tool, you can test the different data you have send threw your topics.

To install MQTT broker, you need to use the following commands :

```bash
  sudo snap install mqtt-explorer # installation of MQTT explorer
```

To launch MQTT, you can either search the application in the ubuntu envirronment or use the following command line :

```bash
  mqtt-explorer
```

# PANDUZA CLIENT

`TODO: Oui mais il faut montrer comment ça marche et non pas comment il est construit`

The panduza client will be the interface between the user and the panduza ecosystem.
The role of the client will be to configure various parameters to send the data of the i/o's to the correct destination.

A digital input output is has various attributs and and fields attached to the those attributs.

```python
  # === DIRECTION ===
  self.add_attribute(
     Attribute( name = "direction" )
  ).add_field(
     RwField( name = "value" )
  ).add_field(
     RwField( name = "pull" )
  ).add_field(
    RwField( name = "polling_cycle" )
  )

  # === STATE ===
  self.add_attribute(
    Attribute( name = "state" )
  ).add_field(
    RwField( name = "active" )
  ).add_field(
    RwField( name = "active_low" )
  ).add_field(
    RwField( name = "polling_cycle" )
  )
```


digital input output has two attributs : direction and state. in each attribut we can add fields that will define the direction and the state of the current I/O.

Those parameters will help us to code the driver functions to get and update the fields.

There is a functionnal python script used to send data to the  gpio 16 of pico via the MQTT broker.
We will set data to each fields by using the get() method.


```python
  from panduza import Client, Dio
  import time, logging


  # CONFIGURATION
  BROKER_ADDR="localhost"
  BROKER_PORT=1883
  CHECK_USER_INPUT=True
  RUN_TEST=False

  # one topic per io
  TOPIC16="pza/my_lab_server/pza_modbus_dio/My_Input_Output_GPIO16"


  testClient = Client(url=BROKER_ADDR, port=1883)
  testClient.connect()

  # scan the interface
  inter = testClient.scan_interfaces()

  # list all the topics
  print("scanning the interfaces..")
  for topic in inter:
      print(f"- {topic} => {inter[topic]['type']}")

    # declare instances of dio. One per io control
    d16 = Dio(addr=BROKER_ADDR, port=BROKER_PORT, topic=TOPIC16, client=testClient)

    print("setting the values for GPIO 16")
    d16.direction.value.set("toggle_led_16", ensure = False)
    time.sleep(1)
    d16.direction.pull.set("open", ensure = False)
    time.sleep(1)
    d16.direction.polling_cycle.set(10, ensure = False)
    time.sleep(1)

    d16.state.active.set(False, ensure = False)
    time.sleep(1)
    d16.state.active_low.set(True, ensure = False)
    time.sleep(1)
    d16.state.polling_cycle.set(100, ensure = False)
    time.sleep(1)

```
This script allows us to control io 16 of the PICO.

There are various steps to configure the client.
First we configure the parameters of the MQTT broker. the address will be "localhost and the listening port is 1883.

Then we declare topics. A topic is a path where the data will be send to the MQTT broker. 
In this example, we will send data to four I/O. It means that we have to create one topic per I/O/


# PANDUZA PLATFORM

`TODO: la platform il faut en parler plus tot et expliquer comment l'utiliser depuis docker, ici c'est trop complexe pour un utilisateur de partir du clone`


The panduza platform is the motor of the panduza eco-system.

It will be the interface where we will develop the drivers and various functions to send data directly to the PICO.

## Architecture of panduza platform

You will have to clone the following repository  and checkout the branch diob: 

```bash
  git clone git@github.com:Panduza/panduza-py.git
  git checkout dio
```


![](../../_media/pza_platform.png)

The meta drivers will declare the set and get functions for each io attributs. The platform will then call those functions, do a first update of the MQTT brocker. Then according to the message of the client, it will call the connector functions to write data to the PICO.

To run the panduza platform you will need to have configuration files : 

one docker-compose.yml
one tree.json

A docker-compose.yml file is a configuration file used by Docker compose. It will run container docker applications.

```yml
version: '3'
services:
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
The most important parameter it image. In this case we will use the local image.

A tree.json file is a specific file in the panduza eco-system. This is used to configure the interfaces to be managed and the associated brokers.
```json
{
    "machine": "my_lab_server",
    "brokers": {
        "I/O driver": {
            "addr": "localhost",
            "port": 1883,
            "interfaces": [
                {
                    "name": "My_Input_Output_GPIO%r",
                    "driver": "pza_modbus_dio",
                    "repeated": [1,2,16,18]
                }
            ]
        }
    }
}
```
For this purpose, we will use the pza_modbus_dio driver witch was declared in the panduza platform driver. 
Also, since a driver is used to control a single IO. The field "repeated" will manage us to declare various instances of a same driver. This tree.json will control GPIO 1, 2, 16 and 18.



# PICO CONFIGURATION

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
  git checkout 2-issue-sur-les-déclarations-des-interfaces-cdc
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

The PICO is now ready to get data from panduza platform.


# RUN PROJECT

Now that the pico is programmed and able to receive data threw modbus. 
We can now run the panduza platform and client.

To run the ecosystem you first need to program the PICO. Then you have to run the platform and excecute the client.

## RUN panduza platform

to run the panduza platform, you first need to build the docker image.

in the panduza-py repository. Go to the platform directory and build the image

```bash
  cd panduza-py/platform # move to platform dir
  ./docker.build-local.sh # build the image
```

The first build may take some time.
Note, the following command can be used if you with rebuild completely the image : 

```bash
  docker build --no-cache --tag local/panduza-py-platform:latest .
```
Once the image is build. You can run the platform.
For this, go to the /deploy/etc_deploy directory

```bash
  cd deploy/etc_panduza
```

then excecute the following command to run the panduza platform

```bash
  docker compose up
```

You must have the following result : 

![](../../_media/docker_compose_up.png)

The docker compose will do a first init of the MQTT broker. This initiation was defined in the driver function.

![](../../_media/log_first_init.png)

Make sure you the topics are visible with the rigth data.


![](../../_media/mqtt_explorer.png)


## RUN panduza client

To run the client, you need to run a client script.
This script can be modify and adaptable for your own purpose.
But it must follow the following architecture.

![](../../_media/architecture_client.png)


Note that one declaration of a topic and Dio interface is used to control a single IO. 
Therefore, if you wish control multiple digital inputs outputs, you will jave to declare various topics and Dio interfaces

The topics declared must match with the topics visible in the mqtt explorer.

A script example is available in the client configuration and explication.

