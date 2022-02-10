Subprocess
===============

MQTT specifications for Panduza Subprocess interfaces.

.. code-block::

  base topic : pza/[machine]/[driver]/[subprocess]


xxx/info
---------

Info is the most basic topic for a Panduza Interface. It explains that this interface will run a process in a subshell.

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
        "type": "shell", "version": "1.0"
    }


xxx/cmds/run
-------------

To run a subprocess

+-----+--------+---------+
| QOS | Retain | Payload |
+=====+========+=========+
| 0   | false  | json    |
+-----+--------+---------+

+-----------+--------+-------------------------------------------+
| Key       | Type   | Description                               |
+===========+========+===========================================+
| process   | string | Name of the process to run with arguments |
+-----------+--------+-------------------------------------------+
| env       | array  | See the tab below for more information    |
+-----------+--------+-------------------------------------------+

+-------+--------+-----------------------------------+
| Key   | Type   | Description                       |
+=======+========+===================================+
| key   | string | Key of the environment variable   |
+-------+--------+-----------------------------------+
| value | string | Value of the environment variable |
+-------+--------+-----------------------------------+

.. code-block:: json

    {
        "process": "ls -a testdir",
        "env": [
            {
                "key": "MY_COM_PORT",
                "value": "/dev/ttyS3"
            },
            {
                "key": "MY_LOGLEVEL",
                "value": "debug"
            }
        ]
    }

xxx/atts/run
-------------

To run a subprocess

+-----+--------+---------+
| QOS | Retain | Payload |
+=====+========+=========+
| 0   | true   | json    |
+-----+--------+---------+

+---------+---------+--------------------------------+
| Key     | Type    | Description                    |
+=========+=========+================================+
| retcode | integer | Return code of the process     |
+---------+---------+--------------------------------+
| stdout  | string  | Standard output of the process |
+---------+---------+--------------------------------+
| stderr  | string  | Standard error of the process  |
+---------+---------+--------------------------------+

.. code-block:: json

    {
        "retcode": 0,
        "stdout": ".\n..\nhello\nworld\n",
        "stderr": ""
    }