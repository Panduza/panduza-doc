---
title: "Install Tools"
date: 2024-05-29T11:15:29+01:00
draft: false
---


# How to start with voxpower inhibitor

### Install git :

https://github.com/git-for-windows/git/releases/download/v2.45.1.windows.1/Git-2.45.1-64-bit.exe \
(Add git path or use git cmd)

### Install python :

https://www.python.org/ftp/python/3.12.3/python-3.12.3-amd64.exe \
On the first page of install click on the "Add python.exe to PATH" button \
Finish install

### Add pip to path :

Add in your variable environment pip path (default path : C:\Python27\Scripts)

To get the python path do : 
```
python
import os
import sys
os.path.dirname(sys.executable)
exit()
```

### Install Rust :

https://static.rust-lang.org/rustup/dist/x86_64-pc-windows-msvc/rustup-init.exe \
(add path)

### Install mosquitto :

https://mosquitto.org/files/binary/win64/mosquitto-2.0.18a-install-windows-x64.exe \
(add path)

### Get platform : 

```
git clone https://github.com/Panduza/panduza-rust-platform.git
```

### Get panduza-py modules :

```
pip install git+https://github.com/Panduza/panduza-py.git
```

### Get flutter app :

https://github.com/Panduza/panduza_sandbox_flutter/actions/runs/9252977096/artifacts/1540496811

### Create basic config mosquitto :

create new file, mosquitto.conf at the location you want \
add these 2 lines inside : 
```
allow_anonymous true
listener 1883
```

### Start mosquitto with basic config :

```
mosquitto -c "your_path_to_mosquitto.conf/mosquitto.conf" -v
```

### Create tree.json :

tree.json path on windows : C:\Users\\"your_user_account_name"\Panduza\tree.json \
tree.json content :
```json
{
    "devices": [
        {
            "ref": "panduza.voxpower_inhibiter",
            "name": "voxpower_inhib",
            "settings": {
                "serial_baudrate": 9600,
                "usb_vendor": "9025",
                "usb_model": "0067"
            }
        }
    ]
}
```

### Create connection.json :

connection.json path on windows : C:\Users\\"your_user_account_name"\Panduza\connection.json \
content connection.json :
```json
{
    "broker":
        {
            "addr":"localhost",
            "port":1883,
            "retry":1
        }, 
    "platform":
        {
            "name": "example"
        }
}
```

### Start platform :

```
cargo run --features trac-fmt
```

### Run endurance test script with flutter app start :

Start flutter app and go add the broker with local discovery 
```
python pza-py-plg-abbelight\examples\002_simple_test_voxpower_inhibiter\endurance_test_4_ping_per_5_s.py
```
