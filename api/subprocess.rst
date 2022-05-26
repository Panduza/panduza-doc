Subprocess
===============

MQTT specifications for Panduza Subprocess interfaces.

.. code-block::

    TYPE: "shell"
    VERSION: "1.0"


Subprocess Topics
--------------------

+----------------+-----+--------+----------------------------+----------------------+
| Suffix         | QOS | Retain | Payload                    | Description          |
+================+=====+========+============================+======================+
| info           | 0   | false  | :ref:`Common Payload Info` | Interface heart beat |
+----------------+-----+--------+----------------------------+----------------------+
| cmds/run       | 0   | true   |                            | To run a subprocess  |
+----------------+-----+--------+----------------------------+----------------------+



- atts/subprocess/retcode
- atts/subprocess/stdout
- atts/subprocess/stderr
- cmds/subprocess/run


Subprocess Payloads
---------------------


Io Payload Run
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~



xxx/cmds/run
-------------



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