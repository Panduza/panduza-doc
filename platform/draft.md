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
                    "name": "My Power Supply",
                    "driver": "hm310t"
                }
            ]
        }
    }
}
```

Test the psu

```bash
pip install https://github.com/Panduza/panduza-py


git clone https://github.com/Panduza/panduza-py


cd panduza-py
python3 tools/psu_test.py -a 192.168.X.X -p 1883

```


