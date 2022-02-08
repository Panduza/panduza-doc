Io
===============

MQTT specifications for Panduza IO interfaces.

.. code-block::

  base topic : pza/[machine]/[driver]/[io]


xxx/info
---------

Info is the most basic topic for a Panduza Interface. It explains that this interface will drive an IO.

+-----+--------+---------+
| QOS | Retain | Payload |
+=====+========+=========+
| 0   | false  | json    |
+-----+--------+---------+

+---------+--------+-----------------------------------------------------------------+
| Key     | Type   | Description                                                     |
+=========+========+=================================================================+
| type    | string | Defines which topics and payloads can be used on this interface |
+---------+--------+-----------------------------------------------------------------+
| version | string | To control the revision of the specification type               |
+---------+--------+-----------------------------------------------------------------+

.. code-block:: json

    {
        "type": "io", "version": "1.0"
    }


xxx/cmds/direction/set
---------------------------------

To set the direction of the IO

+-----+--------+---------+
| QOS | Retain | Payload |
+=====+========+=========+
| 0   | false  | json    |
+-----+--------+---------+

+-----------+--------+-----------------------------------+
| Key       | Type   | Description                       |
+===========+========+===================================+
| direction | string | direction of the io 'in' or 'out' |
+-----------+--------+-----------------------------------+

.. code-block:: json

    {
        "direction": "in"
    }


xxx/cmds/value/set
---------------------------------

To set the value of the IO


+-----+--------+---------+
| QOS | Retain | Payload |
+=====+========+=========+
| 0   | false  | json    |
+-----+--------+---------+

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


xxx/atts/direction
------------------------------------

To get the direction of the IO

+-----+--------+---------+
| QOS | Retain | Payload |
+=====+========+=========+
| 0   | true   | json    |
+-----+--------+---------+

+-----------+--------+-----------------------------------+
| Key       | Type   | Description                       |
+===========+========+===================================+
| direction | string | direction of the io 'in' or 'out' |
+-----------+--------+-----------------------------------+

.. code-block:: json

    {
        "direction": "in"
    }


xxx/atts/value
---------------------------------

To set the value of the IO

+-----+--------+---------+
| QOS | Retain | Payload |
+=====+========+=========+
| 0   | true   | json    |
+-----+--------+---------+

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

