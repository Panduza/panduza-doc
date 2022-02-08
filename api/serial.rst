Serial
===============

MQTT specifications for Panduza serial interfaces.

.. code-block::

  base topic : pza/[host]/[driver]/[serial]


xxx/info
---------

+-----+--------+---------+
| QOS | Retain | Payload |
+=====+========+=========+
| 0   | false  | json    |
+-----+--------+---------+

.. code-block:: json

    {
        "type": "serial", "version": "1.0"
    }


xxx/cmds/data/send
---------------------------------


+-----+--------+------------+
| QOS | Retain | Payload    |
+=====+========+============+
| 0   | false  | byte array |
+-----+--------+------------+


xxx/atts/data
---------------------------------

A new message is published on this topic when data arrived from the serial port.

+-----+--------+------------+
| QOS | Retain | Payload    |
+=====+========+============+
| 0   | false  | byte array |
+-----+--------+------------+


xxx/atts/settings
---------------------------------



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

