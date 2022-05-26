Power Supply
===============

MQTT specifications for Panduza Power Supply interfaces.

.. code-block::

    TYPE: "psu"
    VERSION: "1.0"

Power Supply Topics
--------------------

+----------------+-----+--------+-----------------------------------+------------------------------------------+
| Suffix         | QOS | Retain | Payload                           | Description                              |
+================+=====+========+===================================+==========================================+
| info           | 0   | false  | :ref:`Common Payload Info`        | Interface heart beat                     |
+----------------+-----+--------+-----------------------------------+------------------------------------------+
| atts/state     | 0   | true   | :ref:`Power Supply Payload State` | Current state of the power supply on/off |
+----------------+-----+--------+-----------------------------------+------------------------------------------+
| atts/amps      | 0   | true   | :ref:`Power Supply Payload Amps`  |                                          |
+----------------+-----+--------+-----------------------------------+------------------------------------------+
| atts/volts     | 0   | true   | :ref:`Power Supply Payload Volts` |                                          |
+----------------+-----+--------+-----------------------------------+------------------------------------------+
| cmds/state/set | 0   | false  | :ref:`Power Supply Payload State` | Set the state                            |
+----------------+-----+--------+-----------------------------------+------------------------------------------+
| cmds/amps/set  | 0   | false  | :ref:`Power Supply Payload Amps`  | Set the amps                             |
+----------------+-----+--------+-----------------------------------+------------------------------------------+
| cmds/volts/set | 0   | false  | :ref:`Power Supply Payload Volts` | Set the volts                            |
+----------------+-----+--------+-----------------------------------+------------------------------------------+

Power Supply Payloads
----------------------

Power Supply Payload State
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+-------+--------+-----------------------------------------+
| Key   | Type   | Description                             |
+=======+========+=========================================+
| state | string | state of the power supply 'on' or 'off' |
+-------+--------+-----------------------------------------+

.. code-block:: json

    { state:"on" }

.. code-block:: json

    { state:"off" }


Power Supply Payload Amps
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+------+-------+--------------------------+
| Key  | Type  | Description              |
+======+=======+==========================+
| amps | float | amps of the power supply |
+------+-------+--------------------------+

.. code-block:: json

    { amps: 5 }


Power Supply Payload Volts
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+-------+-------+---------------------------+
| Key   | Type  | Description               |
+=======+=======+===========================+
| volts | float | volts of the power supply |
+-------+-------+---------------------------+

.. code-block:: json

    { volts: 3.3 }

