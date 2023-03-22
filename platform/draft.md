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
version: '3'

services:

  mosquitto:
    image: eclipse-mosquitto
    ports:
      - 1883:1883
      - 9001:9001
    volumes:
      - ./data/mosquitto.conf:/mosquitto/config/mosquitto.conf

  panduza-py-platform:
    image: ghcr.io/panduza/panduza-py-platform:latest
    privileged: true
    network_mode: host
    volumes:
      - .:/etc/panduza
      - /run/udev:/run/udev:ro
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
                    "driver": "pza_modbus_dio"
                }
            ]
        }
    }
}
```

Test the DIO. Make sure Mosquitto service is disabled

```bash
service mosquitto status

```
Build image

```bash
./docker.build-local.sh 
```
Run docker compose

```bash
docker compose up
```

