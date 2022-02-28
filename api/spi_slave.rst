Spi/Slave
===============

MQTT specifications for Panduza Spi Slave interfaces.

.. code-block::

    TYPE: "spi/slave"
    VERSION: "1.0"



Spi Slave Topics
-----------------

+--------------------+-----+--------+---------------------+------------------------------------------+
| Suffix             | QOS | Retain | Payload             | Description                              |
+====================+=====+========+=====================+==========================================+
| info               | 0   | false  | :ref:`Payload Info` | Interface heart beat                     |
+--------------------+-----+--------+---------------------+------------------------------------------+
| atts/settings      | 0   | true   |                     | Spi Configuration                        |
+--------------------+-----+--------+---------------------+------------------------------------------+
| atts/data          | 0   | false  |                     | Data recieved from spi                   |
+--------------------+-----+--------+---------------------+------------------------------------------+
| atts/responses     | 0   | true   |                     | Automatique response when incomming data |
+--------------------+-----+--------+---------------------+------------------------------------------+
| cmds/response/push | 0   | false  |                     | Push a new response in the queue         |
+--------------------+-----+--------+---------------------+------------------------------------------+

The slave has no transfer command, **atts/data** is triggered when data are recieved. User must push **cmds/response/push** responses into a queue.

