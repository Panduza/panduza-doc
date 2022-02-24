Spi Master
===============

MQTT specifications for Panduza Spi Master interfaces.

.. code-block::

    TYPE: "spi/master"
    VERSION: "1.0"


SPI Topics
------------

+-----------------+-----+--------+-------------------------+------------------------+
| Suffix          | QOS | Retain | Payload                 | Description            |
+=================+=====+========+=========================+========================+
| info            | 0   | false  | :ref:`Payload Info`     | Interface heart beat   |
+-----------------+-----+--------+-------------------------+------------------------+
| atts/data       | 0   | false  | :ref:`payload-spi-data` | Data recieved from spi |
+-----------------+-----+--------+-------------------------+------------------------+
| cmds/data/read  | 0   | false  |                         |                        |
+-----------------+-----+--------+-------------------------+------------------------+
| cmds/data/write | 0   | false  |                         |                        |
+-----------------+-----+--------+-------------------------+------------------------+


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


