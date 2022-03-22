Input
===============

MQTT specifications for Panduza input interfaces.

.. code-block::

    TYPE: "input"
    VERSION: "1.0"


Input Topics
--------------------

+---------------+-----+--------+--------------------------------+----------------------+
| Suffix        | QOS | Retain | Payload                        | Description          |
+===============+=====+========+================================+======================+
| info          | 0   | false  | :ref:`Common Payload Info`     | Interface heart beat |
+---------------+-----+--------+--------------------------------+----------------------+
| atts/value    | 0   | false  | :ref:`Spi Master Payload Data` |                      |
+---------------+-----+--------+--------------------------------+----------------------+
| atts/settings | 0   | true   |                                |                      |
+---------------+-----+--------+--------------------------------+----------------------+

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

+------------+----------------------------+---------------------------+
| Key        | Type                       | Description               |
+============+============================+===========================+
| in_request | integer                    | Number of bytes to read   |
+------------+----------------------------+---------------------------+
| out_buffer | string (base64 byte array) | Data that must be written |
+------------+----------------------------+---------------------------+

.. code-block:: json

    {
        "buffer": "dGhpcyBpcyBhIHRlc3Q="
    }

