# Installation to control Digital Input Outputs


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


