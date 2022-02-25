Spi/Master
===============

MQTT specifications for Panduza Spi Master interfaces.

.. code-block::

    TYPE: "spi/master"
    VERSION: "1.0"


Spi Master Topics
--------------------

+----------------------+-----+--------+------------------------------------------+------------------------+
| Suffix               | QOS | Retain | Payload                                  | Description            |
+======================+=====+========+==========================================+========================+
| info                 | 0   | false  | :ref:`Payload Info`                      | Interface heart beat   |
+----------------------+-----+--------+------------------------------------------+------------------------+
| atts/settings        | 0   | false  |                                          | Spi Configuration      |
+----------------------+-----+--------+------------------------------------------+------------------------+
| atts/data            | 0   | false  | :ref:`Spi Master Payload Data`           | Data recieved from spi |
+----------------------+-----+--------+------------------------------------------+------------------------+
| cmds/settings/update | 0   | false  |                                          | Spi Configuration      |
+----------------------+-----+--------+------------------------------------------+------------------------+
| cmds/data/transfer   | 0   | false  | :ref:`Spi Master Payload Data Transfert` |                        |
+----------------------+-----+--------+------------------------------------------+------------------------+

Spi Master Payloads
--------------------

Spi Master Payload Data
~~~~~~~~~~~~~~~~~~~~~~~~~

+--------+--------+-----------------------------------------+
| Key    | Type   | Description                             |
+========+========+=========================================+
| buffer | string | Data bytes converted into base64 string |
+--------+--------+-----------------------------------------+

.. code-block:: json

    {
        "buffer": "dGhpcyBpcyBhIHRlc3Q="
    }


Spi Master Payload Data Transfert
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

TODO
