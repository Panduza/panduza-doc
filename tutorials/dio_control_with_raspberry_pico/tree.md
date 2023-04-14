# Tree 

This page describe the `tree.json` settings file specifications.

This file configure the interfaces that must be managed and the associated brokers.

### [26SA-00] Tree.json

The tree basic structure is a json object that contains the name of the machine and the list of broker configuration.

```json
{
    "machine": "machine_name",
    "brokers": { }
}
```

### [26SA-00] Machine name




## Brokers

### [26SA-00] Broker structure

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

String to set a name to the broker.

### [26SA-00] Broker address

TCP address to access the broker

### [26SA-00] Broker port

TCP Port number to access the broker

### [26SA-00] Broker interfaces



## Interfaces


### [26SA-00] Interface structure

```json
{
    {
        "name": "interface_name",
        "group": "sub_group",
        "driver": "driver_name",
        "thread": "name_of_the_thread",
        "client": "name_of_the_client",
        "repeated": []
    }
}
```

### [26SA-00] Interface name


### [26SA-00] Interface group



### [26SA-00] Interface thread

default for the main thread, else a name

### [26SA-00] Interface client

default for the main broker client, else a name

### [26SA-00] Interface repeated

When the same interface must be declared multiple times with different parameters the `repeated` can be defined.

```json
{
    "repeated": [
        [1, "foo"],
        [2, "psu"],
        [3, "leds"],
    ]
}
```

Then use for each line %N to perform the substitution with N the number of the option

example for the first iteration:

```
%1 == 1
%2 == "foo"
interface_1_foo
```

It means that if you wrote:

```json
{
    {
        "name": "interface_%1_%2",
    }
}
```



