Io
===============

MQTT specifications for Panduza IO interfaces.

.. code-block::

    TYPE: "io"
    VERSION: "1.0"

Io Topics
-----------------

+--------------------+-----+--------+----------------------------+----------------------------------------------------+
| Suffix             | QOS | Retain | Payload                    | Description                                        |
+====================+=====+========+============================+====================================================+
| info               | 0   | false  | :ref:`Common Payload Info` | Interface heart beat                               |
+--------------------+-----+--------+----------------------------+----------------------------------------------------+
| atts/context       | 0   | true   |                            | Information about the real configuration of the Io |
+--------------------+-----+--------+----------------------------+----------------------------------------------------+
| atts/value         | 0   | true   | :ref:`Io Payload Value`    | Current Io value                                   |
+--------------------+-----+--------+----------------------------+----------------------------------------------------+
| atts/direction     | 0   | true   | Current Io direction       | Current Io direction                               |
+--------------------+-----+--------+----------------------------+----------------------------------------------------+
| cmds/value/set     | 0   | false  | :ref:`Io Payload Value`    | To set the Io value                                |
+--------------------+-----+--------+----------------------------+----------------------------------------------------+
| cmds/direction/set | 0   | false  | To set the Io direction    | To set the Io direction                            |
+--------------------+-----+--------+----------------------------+----------------------------------------------------+

Io Payloads
-------------------

Io Payload Value
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+-------+--------+--------------------------------+
| Key   | Type   | Description                    |
+=======+========+================================+
| value | number | Value of the io betwen 0 and 1 |
+-------+--------+--------------------------------+

For digital IO

- 0 low
- 1 high

For Analog IO, the value is a decimal number

.. code-block:: json

    {
        "value": 0
    }

Io Payload Direction
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+-----------+--------+-----------------------------------+
| Key       | Type   | Description                       |
+===========+========+===================================+
| direction | string | direction of the io 'in' or 'out' |
+-----------+--------+-----------------------------------+

.. code-block:: json

    {
        "direction": "in"
    }

