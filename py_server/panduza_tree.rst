Panduza Tree
==============

The Panduza tree aims to describe all the Panduza interfaces that must be mounted on the machine.

Here is an example for rpi4 gpio control.

.. code-block:: json

    {
        "machine": "rpi4_test",
        "brokers": {
            "my_broker": {
                "addr": "192.168.1.100",
                "port": 1883,
                "interfaces": [
                    {
                        "repeated": [
                            2,
                            3,
                            4,
                            14,
                            15,
                            17,
                            27
                        ],
                        "name": "gpio_%r",
                        "driver": "sys_class_gpio",
                        "gpio": {
                            "id": "%r"
                        },
                        "comment": {
                            "GPIO2": "Header Pin 3 (SDA)(Pin 1 is the closest from the SD card, continue the ETH on the same column to get the ood pin values)",
                            "GPIO3": "Header Pin 5 (SCL)",
                            "GPIO4": "Header Pin 7 (GPCLK0)",
                            "GPIO14": "Header Pin 8 (TXD)",
                            "GPIO15": "Header Pin 10 (RXD)",
                            "GPIO17": "",
                            "GPIO27": ""
                        }
                    }
                ]
            }
        }
    }


Tree root attributes
------------------------------

- **machine**: name of the machine on the network. It will be used to create the pza topic pza/[machine]
- **brokers**: list of all the broker reachable by this machine and interfaces that must be bound to it

Interfaces attributes
------------------------------

Interfaces is an array of all the interfaces that must be bounded to the broker.
Each interface declaration must have some common attributes

- **name**: name of the interface 
- **driver**: name of the driver that must be mounted to manage this interface
- **repeated**: this attribut is optional but allow to declare multiple interface of the same type. The interface will be declared for every value of the array remplacing "%r" in strings.


