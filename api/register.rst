Register
============

MQTT specifications for Panduza register interfaces.

.. code-block::

    TYPE: "register"
    VERSION: "1.0"


Register Topics
-----------------

+----------------+-----+--------+----------------------------+----------------------+
| Suffix         | QOS | Retain | Payload                    | Description          |
+================+=====+========+============================+======================+
| info           | 0   | false  | :ref:`Common Payload Info` | Interface heart beat |
+----------------+-----+--------+----------------------------+----------------------+
| atts/state     | 0   | true   |                            |                      |
+----------------+-----+--------+----------------------------+----------------------+
| cmds/reg/write | 0   | false  |                            |                      |
+----------------+-----+--------+----------------------------+----------------------+


Register Payloads
-------------------

Register Payload State
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~



Reset Payload Trigger
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+----------------+---------+--------------------------------------------+
| Key            | Type    | Description                                |
+================+=========+============================================+
| haltAfterReset | boolean | If true this option keep the reset enabled |
+----------------+---------+--------------------------------------------+

.. code-block:: json

    {
        "addr": "",
        "value": "0xff"
    }


