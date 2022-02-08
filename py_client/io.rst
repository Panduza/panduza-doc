Io
==========

This section explains how to use panduza-py to access the Io API.

Control the Io as output
------------------------------

.. code-block:: python

    from panduza import Io

    io = Io(alias="f001")
    io.writeDirection("out")

    # Set pin LOW
    io.writeValue(0)

    # Set pin HIGH
    io.writeValue(1)

