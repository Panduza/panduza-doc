Register Map
==============

MQTT specifications for Panduza register interfaces.

.. code-block::

    TYPE: "register"
    VERSION: "1.0"


Register Topics
-----------------

+------------+-----+--------+----------------------------+---------------------------------+
| Suffix     | QOS | Retain | Payload                    | Description                     |
+============+=====+========+============================+=================================+
| info       | 0   | false  | :ref:`Common Payload Info` | Interface heart beat            |
+------------+-----+--------+----------------------------+---------------------------------+
| atts/map   | 0   | true   |                            | Map of the monitored registers  |
+------------+-----+--------+----------------------------+---------------------------------+
| cmds/read  | 0   | false  |                            | Topic to request register read  |
+------------+-----+--------+----------------------------+---------------------------------+
| cmds/write | 0   | false  |                            | Topic to request register write |
+------------+-----+--------+----------------------------+---------------------------------+
| cmds/watch | 0   | false  |                            | Topic to request register watch |
+------------+-----+--------+----------------------------+---------------------------------+

Register Payloads
-------------------


after cmds/write, the register is written, then the register is read and the value is appenned to atts/map




Register Payload Regs List
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+----------+---------+------------------------------------------------------------------------------+
| Key      | Type    | Description                                                                  |
+==========+=========+==============================================================================+
| addr     | string  | Address of the register                                                      |
+----------+---------+------------------------------------------------------------------------------+
| value    | string  | Value of the register                                                        |
+----------+---------+------------------------------------------------------------------------------+
| pollTime | integer | Time between 2 polling of the register in millisecond, -1 to disable polling |
+----------+---------+------------------------------------------------------------------------------+
| width    | integer | Number of byte that compose the register                                     |
+----------+---------+------------------------------------------------------------------------------+

.. code-block:: json

    {
        "regs": [
            { "addr": "0x4242", "value": "0xff", "pollTime": 5, width: [1,2,4,8] }
        ]
    }


