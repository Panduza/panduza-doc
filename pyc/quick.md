# Python Client Quick Start

This quick guide will show you how to interact with a Panduza server.

## Prerequisites

- Windows or Linux
- python3
- pip 

## Installation

First you need to install the python client.

```bash
pip install -e "git+https://github.com/Panduza/panduza-py.git@main#egg=panduza&subdirectory=client"
```

## Scan the server interfaces

Panduza server let you scan available interfaces:

```python
from panduza import Client

# Do not forget to remplace the IP and PORT by the one you target
# c = Client(url="localhost", port=1883)
c = Client(url="192.168.1.4", port=1883)

# Then connect and scan
c.connect()
c.scan_interfaces()
```

You should see something like this:

```bash
{'pza/xdocz_lab/platform/py': {'type': 'platform', 'version': '0.0', 'state': 'run', 'interfaces': 3}, 'pza/xdocz_lab/arduino/serial': {'type': 'serial', 'version': '1.0', 'state': 'run'}, 'pza/xdocz_lab/arduino/power': {'type': 'psu', 'version': '1.0', 'state': 'run'}}
```

Each panduza interface has at least a topic and a type.

```python
# List interface topics and types
interfaces = c.scan_interfaces()
for topic in interfaces:
    print(f"- {topic} => {interfaces[topic]['type']}")
```

A possible result is the following and will be used for the rest of this guide.

- pza/xdocz_lab/platform/py => platform
- pza/xdocz_lab/arduino/power => psu
- pza/xdocz_lab/arduino/serial => serial

## Drive a Power Supply

```python
from panduza import Psu

# Connect to the interface
p = Psu(addr="192.168.1.4", port=1883, topic='pza/xdocz_lab/arduino/power')

# Set to 5 volts
p.volts.value.set(5)

# Turn on
p.state.value.set("on")

# Set to 8.65 volts
p.volts.value.set(8.65)

# Turn off
p.state.value.set("off")
```

## Use the serial port

```python
from panduza import Serial

# Connect to the interface
s = Serial(addr="192.168.1.4", port=1883, topic='pza/xdocz_lab/arduino/serial')
# WARNING : every data recieved before the connection to the interface is lost
# So make sur you have created this interface soon enough in your script

# Read data from the serial port
data = s.read()
print(data)

# Write data
s.write(b"hello !!\n")
```

