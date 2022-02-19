SPI
===============

MQTT specifications for Panduza SPI interfaces.


SPI Topics
------------

+----------------+-----+--------+-------------------------+--------------------------------------+
| Suffix         | QOS | Retain | Payload                 | Description                          |
+================+=====+========+=========================+======================================+
| info           | 0   | false  | :ref:`Payload Info`     | Interface heart beat                 |
+----------------+-----+--------+-------------------------+--------------------------------------+
| atts/data      | 0   | false  | :ref:`payload-spi-data` | To recieve packet from the interface |
+----------------+-----+--------+-------------------------+--------------------------------------+
| cmds/data/send | 0   | false  | :ref:`payload-spi-data` | To send packet on the interface      |
+----------------+-----+--------+-------------------------+--------------------------------------+


SPI Payloads
--------------

.. _payload-spi-data:

SPI Payload Data
~~~~~~~~~~~~~~~~~~~~~~

+--------+--------+-----------------------------------------+
| Key    | Type   | Description                             |
+========+========+=========================================+
| buffer | string | Data bytes converted into base64 string |
+--------+--------+-----------------------------------------+

.. code-block:: json

    {
        "buffer": "dGhpcyBpcyBhIHRlc3Q="
    }


