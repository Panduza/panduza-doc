Power Supply
===============

MQTT specifications for Panduza Power Supply interfaces.

.. code-block::

    type: "psu"
    version: "1.0"

Power Supply Topics
--------------------

+-------------------+-----+--------+-------------------------------------------+-----------------------------------------------+
| Suffix            | QOS | Retain | Payload                                   | Description                                   |
+===================+=====+========+===========================================+===============================================+
| info              | 0   | false  | :ref:`Common Payload Info`                | Interface heart beat                          |
+-------------------+-----+--------+-------------------------------------------+-----------------------------------------------+
| atts/state        | 0   | true   | :ref:`Power Supply Payload State`         | Actual state of the power supply on/off       |
+-------------------+-----+--------+-------------------------------------------+-----------------------------------------------+
| atts/amps         | 0   | true   | :ref:`Power Supply Payload Atts Amps`     | Attributes related to current                 |
+-------------------+-----+--------+-------------------------------------------+-----------------------------------------------+
| atts/volts        | 0   | true   | :ref:`Power Supply Payload Atts Volts`    | Attributes related to voltage                 |
+-------------------+-----+--------+-------------------------------------------+-----------------------------------------------+
| atts/settings     | 0   | true   | :ref:`Power Supply Payload Settings`      | Attibutes related to settings                 |
+-------------------+-----+--------+-------------------------------------------+-----------------------------------------------+
| cmds/state/set    | 0   | false  | :ref:`Power Supply Payload State`         | Set the state value                           |
+-------------------+-----+--------+-------------------------------------------+-----------------------------------------------+
| cmds/amps/set     | 0   | false  | :ref:`Power Supply Payload Cmd Amps`      | Set the amps value                            |
+-------------------+-----+--------+-------------------------------------------+-----------------------------------------------+
| cmds/volts/set    | 0   | false  | :ref:`Power Supply Payload Cmd Volts`     | Set the volts value                           |
+-------------------+-----+--------+-------------------------------------------+-----------------------------------------------+
| cmds/settings/set | 0   | false  | :ref:`Power Supply Payload Settings`      | Set the settings                              |
+-------------------+-----+--------+-------------------------------------------+-----------------------------------------------+

Power Supply Payloads
----------------------

Power Supply Payload Cmd Amps
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+------+-------+--------------------------+
| Key  | Type  | Description              |
+======+=======+==========================+
| amps | float | amps of the power supply |
+------+-------+--------------------------+

.. code-block:: json

    { "amps": 5 }


Power Supply Payload Cmd Volts
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+-------+-------+---------------------------+
| Key   | Type  | Description               |
+=======+=======+===========================+
| volts | float | volts of the power supply |
+-------+-------+---------------------------+

.. code-block:: json

    { "volts": 3.3 }

Power Supply Payload State
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+-------+--------+-----------------------------------------+
| Key   | Type   | Description                             |
+=======+========+=========================================+
| state | string | state of the power supply 'on' or 'off' |
+-------+--------+-----------------------------------------+

.. code-block:: json

    { "state":"on" }

.. code-block:: json

    { "state":"off" }


Power Supply Payload Atts Amps
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+------+-------+-----------------------------------------+
| Key  | Type  | Description                             |
+======+=======+=========================================+
| amps | JSON  | Current information of the power supply |
+------+-------+-----------------------------------------+

The JSON object format for amps is the following

+-------+-------+--------------------------------------+
| Key   | Type  | Description                          |
+=======+=======+======================================+
| value | float | current value                        |
+-------+-------+--------------------------------------+
| min   | float | minimum amps value allowed           |
+-------+-------+--------------------------------------+
| max   | float | maximum amps value allowed           |
+-------+-------+--------------------------------------+
| scale | float | precision of step for current value  |
|       |       |                                      |
|       |       | (1 = 1 amps, 0.001 = 1 milliamp)     |
+-------+-------+--------------------------------------+

For a power supply supporting current range from 0 amps to 5 amps with a precision of one milliamp.

.. code-block:: json

    {
        "amps": {
            "value": 1.25,
            "min": 0,
            "max": 5,
            "scale": 0.001,
        }
    }

Power Supply Payload Atts Volts
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+-------+-------+------------------------------------------+
| Key   | Type  | Description                              |
+=======+=======+==========================================+
| volts | JSON | Voltage information of the power supply   |
+-------+-------+------------------------------------------+

The JSON object format for volts is the following

+-------+-------+------------------------------------+
| Key   | Type  | Description                        |
+=======+=======+====================================+
| value | float | voltage value                      |
+-------+-------+------------------------------------+
| min   | float | minimum volts value allowed        |
+-------+-------+------------------------------------+
| max   | float | maximum volts value allowed        |
+-------+-------+------------------------------------+
| scale | float | precision of step for votls value  |
|       |       |                                    |
|       |       | (1 = 1 volt, 0.001 = 1 millivolt)  |
+-------+-------+------------------------------------+


For a power supply supporting voltage range from 0 volts to 30 volts with a precision of a tens of volts.

.. code-block:: json

    {
        "volts": {
            "value": 3.3,
            "min": 0,
            "max": 30,
            "scale": 0.1,
        }
    }

Power Supply Payload Settings
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+----------+-------+---------------------------------+
| Key      | Type  | Description                     |
+==========+=======+=================================+
| settings | JSON  | settings of the power supply    |
+----------+-------+---------------------------------+

The Power Supply API offers a defined list of settings.

Each power supply has its own supported settings, and may only use a certain amount of these settings.

The JSON object published as an attribute by the server will contain all the supported settings by this specific power supply.

API available settings are as follow

+----------------+---------+------------------------------------------------------------------------+
| key            | Type    | Description                                                            |
+================+=========+========================================================================+
| serial_port    | string  | TTY file for serial communication                                      |
+----------------+---------+------------------------------------------------------------------------+
| ovp            | boolean | Enables over voltage protection                                        |
+----------------+---------+------------------------------------------------------------------------+
| ocp            | boolean | Enables over current protection                                        |
+----------------+---------+------------------------------------------------------------------------+
| silent         | boolean | Enables silent mode (some power supplies can disable speaker)          |
+----------------+---------+------------------------------------------------------------------------+
| refresh_period | float   | Sets the period in seconds to fetch informations from the PSU          |
+----------------+---------+------------------------------------------------------------------------+

WARNING ! refresh_period is not implemented yet and will be ignored.

.. code-block:: json

    { 
        "settings": {
            "serial_port": "/dev/ttyACM0",
            "ocp": false,
            "ovp": true,
            "refresh_period": 0,
            "silent": true
        }
    }

