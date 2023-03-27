## Manual installation

Create the directory /etc/panduza on your server

```bash
sudo mkdir -p /etc/panduza
```

Create the file for docker-compose

```bash
sudo touch /etc/panduza
```

fill it with the given content

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

Create a tree.json

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

Test the DIO. Make sure Mosquitto service is inactive

```bash
service mosquitto stop
service mosquitto status

```
Build image

```bash
docker build --no-cache --tag local/panduza-py-platform:latest . 

```
Run docker compose

```bash
docker compose up
```

