Spi/Master
===============

MQTT specifications for Panduza Spi Master interfaces.

.. code-block::

    TYPE: "spi/master"
    VERSION: "1.0"


Spi Master Topics
--------------------

+--------------------+-----+--------+------------------------------------------+------------------------+
| Suffix             | QOS | Retain | Payload                                  | Description            |
+====================+=====+========+==========================================+========================+
| info               | 0   | false  | :ref:`Payload Info`                      | Interface heart beat   |
+--------------------+-----+--------+------------------------------------------+------------------------+
| atts/settings      | 0   | true   |                                          | Spi Configuration      |
+--------------------+-----+--------+------------------------------------------+------------------------+
| atts/data          | 0   | false  | :ref:`Spi Master Payload Data`           | Data recieved from spi |
+--------------------+-----+--------+------------------------------------------+------------------------+
| cmds/data/transfer | 0   | false  | :ref:`Spi Master Payload Data Transfert` |                        |
+--------------------+-----+--------+------------------------------------------+------------------------+

Spi Master Payloads
--------------------

Spi Master Payload Data
~~~~~~~~~~~~~~~~~~~~~~~~~

+---------------+--------+-----------------------------------------+
| Key           | Type   | Description                             |
+===============+========+=========================================+
| data_received | string | Data bytes converted into base64 string |
+---------------+--------+-----------------------------------------+

.. code-block:: json

    {
        "data_received": "dGhpcyBpcyBhIHRlc3Q="
    }


Spi Master Payload Data Transfert
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+-----------------+----------------------------+---------------------------+
| Key             | Type                       | Description               |
+=================+============================+===========================+
| size_to_receive | integer                    | Number of bytes to read   |
+-----------------+----------------------------+---------------------------+
| data_to_send    | string (base64 byte array) | Data that must be written |
+-----------------+----------------------------+---------------------------+

.. code-block:: json

    {
        "size_to_receive": 4,
        "data_to_send": "dGhpcyBpcyBhIHRlc3Q="
    }

