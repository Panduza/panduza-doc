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


Payload Info
--------------------------------------------

.. code-block:: json

    {
        "type": "example", "version": "x.y"
    }


pza/[machine]/[driver]/[interface]/info
--------------------------------------------

This topic must be published by every interface every 2s. It provides a way to get all the reachable interfaces.

+-----+--------+---------+
| QOS | Retain | Payload |
+=====+========+=========+
| 0   | false  | json    |
+-----+--------+---------+

.. code-block:: json

    {
        "type": "example", "version": "x.y"
    }

