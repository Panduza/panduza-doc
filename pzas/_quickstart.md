# Panduza Server Quick Start

This quick guide will show you how to implement a Panduza server.

## Prerequisites

- A virtual machine with Ubuntu 22.04

## Installation

First you need to install docker and docker compose.

Click on the following link to install docker: https://docs.docker.com/engine/install/ubuntu/

Click on the following link to install docker compose: https://docs.docker.com/compose/install/linux/#install-the-plugin-manually


Add your username to the docker group:

``` bash
    sudo usermod -aG docker $USER 

```
## On your server

Create the repository /etc/panduza:

``` bash
    sudo mkdir -p /etc/panduza

```
Inside this repository, create the file docker-compose.yml:


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
    
    # To use your local platform build
    image: ghcr.io/panduza/panduza-py-platform:latest
    privileged: true
    network_mode: host
    volumes:
      - .:/etc/panduza
      - /run/udev:/run/udev:ro
    

```

In the same repository, create a file "tree.json": 

``` json
{
    "machine": "rename_this_machine",
    "brokers": {
        "test_broker": {
            "addr": "localhost",
            "port": 1883,
            "interfaces": [
                
                {
                    "name": "fake_io",
                    "driver": "fake_io",
                    "settings" : {
                        "mode": 1,
                        "port_name" : "/2"
                    },
                    "pin" : num_pin
                },

            ]
        }
    }
}

```
Note that you should fill the parameters such as « name » « driver » and « settings » according to what you want to do using the panduza platform. 

Create the repository /etc/panduza/data:

``` bash
    sudo mkdir -p /etc/panduza/data

```

In the /etc/panduza/data repository, create the file mosquitto.conf:

``` bash
#
allow_anonymous true

#
listener 1883 0.0.0.0

#
listener 9001 0.0.0.0
protocol websockets

```




## Clone the panduza repository

 Clone the Panduza-py repository.


``` bash
    git clone git@github.com:Panduza/panduza-py.git

```

## Launch the docker containers

In your repository /etc/panduza, enter the following command:

```bash
docker-compose up
```

