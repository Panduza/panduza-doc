# Panduza Server Quick Start

This quick guide will show you how to implement a Panduza server.

## Prerequisites

- A virtual machine with Ubuntu 22.04
- python3
- pip 

## Installation

First you need to install docker and docker compose.

Click on the following link to install docker: https://docs.docker.com/engine/install/ubuntu/

Click on the following link to install docker compose: https://docs.docker.com/compose/install/linux/#install-the-plugin-manually

Install MQTT explorer with the following command:

``` bash
    sudo snap install mqtt-explorer

```

Add your username to the docker group:

``` bash
    sudo usermod -aG docker $USER 

```


## Clone the panduza repository and updtate files

You will need to update files of the panduza repository to launch your server.


In /Documents, clone the Panduza-py repository on the branch "update-ftdi-io":


``` bash
    git clone -b update-ftdi-io  git@github.com:Panduza/panduza-py.git

```


## Update the files

Modify the /panduza-py/platform/deploy/etc_panduza/docker-compose.yml to match the following picture:

``` yml
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
    #image: ghcr.io/panduza/panduza-py-platform:latest
    # To use your local platform build
    image: local/panduza-py-platform
    privileged: true
    network_mode: host
    volumes:
      - .:/etc/panduza
      - /run/udev:/run/udev:ro
    # command: bash

```

Modify the file /panduza-py/platform/deploy/etc_panduza/tree.json to match the following code: 

``` json
{
    "machine": "rename_this_machine",
    "brokers": {
        "test_broker": {
            "addr": "localhost",
            "port": 1883,
            "interfaces": [
                
                {
                    "name": "ftdi5",
                    "driver": "ftdi_io",
                    "settings" : {
                        "mode": 1,
                        "port_name" : "/2"
                    },
                    "pin" : 4
                },
                {
                    "name": "fake_io",
                    "driver": "fake_io"
                }
            ]
        }
    }
}

```
Please note that you should fill the parameters such as « name » « driver » and « settings » according to what you want to do using the panduza platform. 

In the file /panduza-py/platform/Dockerfile, add the following line in the pip installation section :

``` bash
RUN pip install pyftdi
```

In the file /panduza-py/platform/Dockerfile, under the installation of udev, add:

``` bash
RUN apt-get -y install udev libusb-1.0-0
```

In the import section (at the top of the file) of the file panduza_platform/connectors/ftdi.py add:

``` python
from pyftdi.gpio import GpioController
```

In the constructor of the class "ConnectorFtdiGpio", replace 

``` python
self.__internal_driver=Ftdi()
```
by 

``` python
self.__internal_driver=GpioController()
```

## Generate the Panduza image

In the directory /panduza-py/platform/ generate the panduza-py-platform:latest with the following command:

```bash
./docker.build-local.sh
```

## Launch the docker containers

In the repository /panduza-py/platform/deploy/etc_panduza :

```bash
docker-compose up
```

