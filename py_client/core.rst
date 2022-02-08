Core
=======


Configure Aliases
------------------------------

Instead of using the broker url and a base topic every time. Alias allow you to use a short name to refer to an interface.

.. code-block:: python

    from panduza import Core

    Core.LoadAliases(
    {
        "connection_1":
        {
            "url": "localhost",
            "port": 1883,
            "interfaces": {
                "foo1": "pza/host/client/foo1"
                "foo2": "pza/host/client/foo2"
            }
        }        
    })



