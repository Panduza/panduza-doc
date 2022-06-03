Reset
===============

MQTT specifications for Panduza reset interfaces.

.. code-block::

    TYPE: "reset"
    VERSION: "1.0"

Reset Topics
-----------------

+--------------------+-----+--------+------------------------------+----------------------+
| Suffix             | QOS | Retain | Payload                      | Description          |
+====================+=====+========+==============================+======================+
| info               | 0   | false  | :ref:`Common Payload Info`   | Interface heart beat |
+--------------------+-----+--------+------------------------------+----------------------+
| atts/state         | 0   | true   | :ref:`Reset Payload State`   | Current reset state  |
+--------------------+-----+--------+------------------------------+----------------------+
| cmds/reset/trigger | 0   | false  | :ref:`Reset Payload Trigger` | To trigger the reset |
+--------------------+-----+--------+------------------------------+----------------------+


Reset Payloads
-------------------

Reset Payload State
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+-------+--------+-------------------------------------------+
| Key   | Type   | Description                               |
+=======+========+===========================================+
| value | string | Value of the state : resetting or running |
+-------+--------+-------------------------------------------+

.. code-block:: json

    {
        "value": "running"
    }

Reset Payload Trigger
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+----------------+---------+--------------------------------------------+
| Key            | Type    | Description                                |
+================+=========+============================================+
| haltAfterReset | boolean | If true this option keep the reset enabled |
+----------------+---------+--------------------------------------------+

.. code-block:: json

    {
        "keepReset": false
    }

