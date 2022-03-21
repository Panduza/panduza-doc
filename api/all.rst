Common
===============

This section describes topics and payloads common for all Panduza Mqtt clients.

Panduza levels are defined as follow

.. code-block::

    FORMAT: pza/[machine]/[driver]/[interface]/[specifier]/[attribut]

- **pza**       : to tag all the topics matching the Panduza specification
- **machine**   : defines the host on which the driver is located. It should be the name of the physical device that support the driver.
- **driver**    : defines the name of the driver that support this interface. It should be the name of the process running the driver.
- **interface** : defines the interface name.
- **specifier** : [atts|cmds|info]
- **attribut**  : defines the specific element of the interface to monitor.


Common Topics
--------------------

Here are the common interface topics

+--------+-----+--------+------------------------------+----------------------+
| Suffix | QOS | Retain | Payload                      | Description          |
+========+=====+========+==============================+======================+
| info   | 0   | false  | :ref:`Common Payload Info`   | Interface heart beat |
+--------+-----+--------+------------------------------+----------------------+
| status | 0   | true   | :ref:`Common Payload Status` | Interface status     |
+--------+-----+--------+------------------------------+----------------------+


Common Payload Info
--------------------------------------------

This topic must be published by every interface every 2s. It provides a way to get all the reachable interfaces.

.. code-block:: json

    {
        "type": "example", "version": "x.y"
    }


Common Payload Status
--------------------------------------------

+---------+--------+-----------------------------------------------+
| Key     | Type   | Description                                   |
+=========+========+===============================================+
| status  | string | Status of the interface (see standart status) |
+---------+--------+-----------------------------------------------+
| comment | string | Context information for the status            |
+---------+--------+-----------------------------------------------+

.. code-block:: json

    {
        "status": "ready",
        "comment": "context for the status"
    }


