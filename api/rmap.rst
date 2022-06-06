Register Map
==============

MQTT specifications for Panduza register interfaces.

.. code-block::

    TYPE: "rmap"
    VERSION: "1.0"


Register Topics
-----------------

+-----------------+-----+--------+----------------------------+---------------------------------+
| Suffix          | QOS | Retain | Payload                    | Description                     |
+=================+=====+========+============================+=================================+
| info            | 0   | false  | :ref:`Common Payload Info` | Interface heart beat            |
+-----------------+-----+--------+----------------------------+---------------------------------+
| atts/map        | 0   | true   |                            |                                 |
+-----------------+-----+--------+----------------------------+---------------------------------+
| atts/settings   | 0   | true   |                            |                                 |
+-----------------+-----+--------+----------------------------+---------------------------------+
| cmds/regs/read  | 0   | false  |                            |                                 |
+-----------------+-----+--------+----------------------------+---------------------------------+
| cmds/regs/write | 0   | false  |                            | Topic to request register write |
+-----------------+-----+--------+----------------------------+---------------------------------+


Register Payloads
-------------------



Register Map Payload Settings
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+---------------+--------+-------------------------------+
| Key           | Type   | Description                   |
+===============+========+===============================+
| base_addr     | string | Address of the first register |
+---------------+--------+-------------------------------+
| reg_width     | int    | With of registers in bytes    |
+---------------+--------+-------------------------------+
| reg_number    | int    | Number of register in the map |
+---------------+--------+-------------------------------+
| poll_interval | number | Time between 2 map reading    |
+---------------+--------+-------------------------------+

.. code-block:: json

    {
        "base_addr": "0x8000",
        "reg_width": 4,
        "reg_number": 20,
        "poll_interval": 
    }




Register Payload Regs List
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+---------+--------+-------------------------+
| Key     | Type   | Description             |
+=========+========+=========================+
| address | string | Address of the register |
+---------+--------+-------------------------+
| value   | string | Value of the register   |
+---------+--------+-------------------------+

.. code-block:: json

    {
        "regs": [
            { "addr": "0x4242", "value": "0xff" }
        ]
    }


