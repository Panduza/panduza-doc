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

    # Install the platform
    sudo pip install panduza_platform

    # Deploy systemd service files
    sudo wget  -O /etc/systemd/system/panduza-py-platform.service  https://raw.githubusercontent.com/Panduza/panduza-py-platform/main/deploy/panduza-py-platform.service
    sudo wget  -O /usr/local/bin/pza-py-platform-run.py  https://raw.githubusercontent.com/Panduza/panduza-py-platform/main/deploy/pza-py-platform-run.py
    sudo chmod +x /usr/local/bin/pza-py-platform-run.py
    sudo systemctl daemon-reload


Then let's mount a FakeIO interface. Interfaces must be declared in the configuration file: */etc/panduza/tree.json*

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
    
.. code-block:: bash
    
    sudo systemctl restart panduza-py-platform.service


