Can
===============

MQTT specifications for Panduza can interfaces.

.. code-block::

  base topic : pza/[host]/[driver]/[can]


xxx/info
---------

+-----+--------+---------+
| QOS | Retain | Payload |
+=====+========+=========+
| 0   | false  | json    |
+-----+--------+---------+

.. code-block:: json

    {
        "type": "can", "version": "1.0"
    }


xxx/cmds/msg
---------------------------------


+-----+--------+---------+
| QOS | Retain | Payload |
+=====+========+=========+
| 0   | false  | json    |
+-----+--------+---------+

.. code-block:: json

    {
        "type": "msg", 
        "id": 1,
        "length": 4,
        "payload": [
            0,
            1,
            2,
            3
        ]
    }


xxx/atts/msg
---------------------------------

A new message is published on this topic when data arrived from the can bus.

+-----+--------+---------+
| QOS | Retain | Payload |
+=====+========+=========+
| 0   | false  | json    |
+-----+--------+---------+

.. code-block:: json

    {
        "id": 1,
        "length": 4,
        "payload": [
            0,
            1,
            2,
            3
        ]
    }

xxx/atts/settings
---------------------------------

TODO

xxx/atts/settings/port
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+-----+--------+------------+
| QOS | Retain | Payload    |
+=====+========+============+
| 0   | true   | string     |
+-----+--------+------------+


xxx/atts/settings/baudrate
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+-----+--------+------------+
| QOS | Retain | Payload    |
+=====+========+============+
| 0   | true   | number     |
+-----+--------+------------+

