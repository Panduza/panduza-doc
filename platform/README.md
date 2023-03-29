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

