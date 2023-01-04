# Quick Start

This quick guide will show you how to interact with a Panduza server.

## Prereq

pip 


## Installation

First you need to install the python client.

```bash
pip install -e "git+https://github.com/Panduza/panduza-py.git@main#egg=panduza&subdirectory=client"
```

## Scan the server interfaces

```python
from panduza import Client
c = Client(url="localhost", port=1883)
c = Client(url="192.168.1.4", port=1883)
c.connect()
c.scan_interfaces()
```

## Drive a Power Supply

```python
from panduza import Psu
p = Psu(addr="192.168.1.4", port=1883, topic='pza/alien/hanmatek.hm310t/HM310T')
p.volts.value.set(5)

p.state.value.set("on")
```



