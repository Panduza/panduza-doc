Platform
===============

.. code-block::

    TYPE: "platform"
    VERSION: "1.0"


Platform Topics
-----------------

+----------------+-----+--------+---------------------+----------------------------------------+
| Suffix         | QOS | Retain | Payload             | Description                            |
+================+=====+========+=====================+========================================+
| info           | 0   | false  | :ref:`Payload Info` | Interface heart beat                   |
+----------------+-----+--------+---------------------+----------------------------------------+
| atts/tree      | 0   | false  | :ref:`payload-tree` | To get the Panduza tree of the machine |
+----------------+-----+--------+---------------------+----------------------------------------+
| cmds/tree/load | 0   | false  | :ref:`payload-tree` |                                        |
+----------------+-----+--------+---------------------+----------------------------------------+

Platform Payloads
-------------------

.. _payload-tree:

Platform Payload Data
~~~~~~~~~~~~~~~~~~~~~~~~~

+---------+--------+----------------------------------+
| Key     | Type   | Description                      |
+=========+========+==================================+
| machine | string |                                  |
+---------+--------+----------------------------------+
| brokers | object | Interfaces declaration by broker |
+---------+--------+----------------------------------+

.. code-block:: json

    {
        "machine": "name_of_the_machine",
        "brokers": {
            "name_of_the_first_broker": {
                "addr": "192.168.1.100",
                "port": 1883,
                "interfaces": [
                ]
            }
        }
    }



