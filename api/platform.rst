Platform
===============

.. code-block::

    TYPE: "platform"
    VERSION: "1.0"


Platform Topics
-----------------

+------------------+-----+--------+---------------------------------+------------------------------------------+
| Suffix           | QOS | Retain | Payload                         | Description                              |
+==================+=====+========+=================================+==========================================+
| info             | 0   | false  | :ref:`Common Payload Info`      | Interface heart beat                     |
+------------------+-----+--------+---------------------------------+------------------------------------------+
| atts/drivers     | 0   | false  | :ref:`Platform Payload Drivers` | To get drivers available in the platform |
+------------------+-----+--------+---------------------------------+------------------------------------------+
| atts/tree        | 0   | false  |                                 |                                          |
+------------------+-----+--------+---------------------------------+------------------------------------------+
| cmds/tree/update | 0   | false  |                                 |                                          |
+------------------+-----+--------+---------------------------------+------------------------------------------+

Platform Payloads
-------------------

Platform Payload Drivers
~~~~~~~~~~~~~~~~~~~~~~~~~

todo


Platform Payload Tree Update
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

By default, this command will try to merge the current loaded tree with the tree you provide in this command.
The goal is to preserve the current loading interface, unless you specify otherwise.

+---------+--------------+-------------+
| Key     | Type         | Description |
+=========+==============+=============+
| tree    | object       |             |
+---------+--------------+-------------+
| options | string array |             |
+---------+--------------+-------------+

.. code-block:: json

    {
        "tree": { the tree structure you want to load },
        "options": [   ]
    }

**Override Options**

!!! This commands can cut you from the platform !!!
To be sure that it is want you want, you need to pass confirmation options to override the default (safe) behaviour.

- "override_machine_name": allow the command to override the "machine_name"
- "replace_brokers": delete old brokers and put yours instead

**Merge Strategy**

To merge **current_tree** and **new_tree** here is the algorithm used:

.. code-block:: cpp
    
    // Manage machine name
    if (override_machine_name) {
        current_tree.machine_name = new_tree.machine_name
    }

    // Manage brokers total overriding
    if (replace_brokers) {
        current_tree.brokers.delete_all()
    }

    // Merge new brokers
    for (new_broker  in  new_tree.brokers) {

        if (new_broker.name exist in current_tree.brokers) {
            merge interfaces
        }

    }

    reload(current_tree)
