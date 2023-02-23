# Tree 




### [26SA-00] Tree.json

The tree basic structure is a json object that contains the name of the machine and the list of broker configuration

```json
{
    "machine": "machine_name",
    "brokers": { }
}
```


## Brokers

```json
{
    "brokers": {
        "name_of_the_broker": {
            "addr": "localhost",
            "port": 1883,
            "interfaces": [ { interface } ... ]
        }
    }
}
```

### [26SA-00] Broker name
### [26SA-00] Broker port
### [26SA-00] Broker interfaces


## Interfaces

```json
{
    {
        "name": "interface_name",
        "group": "sub_group",
        "driver": "driver_name",
        "thread": "name_of_the_thread",
        "client": "name_of_the_client",
    }
}
```

### [26SA-00] Interface name

### [26SA-00] Interface thread

default for the main thread, else a name

### [26SA-00] Interface client

default for the main broker client, else a name


