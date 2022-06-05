Fake Overview
================

Panduza aims to abstract hardware interfaces. This abstraction concept allows Panduza to create fake interfaces that responds like real interfaces.
This is a good way to start Panduza initiation because it requires only a Ubuntu computer and few software setup.

Setup Python Platform
------------------------

The first thing to do is to setup the python platform.

.. code-block:: bash

    # Install python3
    sudo apt-get install python3 python3-pip

    # Install the platform and the python clients
    sudo pip install panduza_platform panduza

    # Deploy systemd service files
    sudo wget  -O /etc/systemd/system/panduza-py-platform.service  https://raw.githubusercontent.com/Panduza/panduza-py-platform/main/deploy/panduza-py-platform.service
    sudo wget  -O /usr/local/bin/pza-py-platform-run.py  https://raw.githubusercontent.com/Panduza/panduza-py-platform/main/deploy/pza-py-platform-run.py
    sudo chmod +x /usr/local/bin/pza-py-platform-run.py
    sudo systemctl daemon-reload


Configure the tree
------------------------

Then let's mount a FakeIO interface. Interfaces must be declared in the configuration file:

*/etc/panduza/tree.json*

.. code-block:: json

    {
        "machine": "my_test_machine",
        "brokers": {
            "my_broker": {
                "addr": "localhost",
                "port": 1883,
                "interfaces": [
                    {
                        "name": "my_first_fake_io",
                        "driver": "fake_io"
                    }
                ]
            }
        }
    }

Then you have to restart the platform toload the new tree

.. code-block:: bash

    # Restart the platform service    
    sudo systemctl restart panduza-py-platform.service


Use the python client
------------------------


.. code-block:: python

    from panduza import Core, Io

    Core.LoadAliases(
    {
        "connection_1":
        {
            "url": "localhost",
            "port": 1883,
            "interfaces": {
                "my_first_fake_io": "pza/my_test_machine/fake_io/my_first_fake_io"
            }
        }        
    })


    io = Io(alias="my_first_fake_io")
    io.writeDirection("out")

    # Set pin LOW
    io.writeValue(0)

    # Set pin HIGH
    io.writeValue(1)

