Can
==========

This section explains how to use panduza-py to access the Can API.

Read message from Can bus
------------------------------

.. code-block:: python

    from panduza import Can

    s = Can(alias="canBus")

    def _on_data(data):
        msg = json.loads(data)
        print(f"{hex(msg['canId'])[2:].zfill(3).upper()} [{msg['length']}] {' '.join(str(hex(x)[2:].zfill(2).upper()) for x in msg['payload'])}")

    s.read_loop(_on_data)

Write message to Can bus
------------------------------

.. code-block:: python

    from panduza import Can

    s = Can(alias="canBus")

    s.write(0xAA, [1,2])

