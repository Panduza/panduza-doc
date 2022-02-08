Meta Driver
=============

Meta drivers are used by the quick server to manage all the possible interfaces.


Create your custom MetaDriver
-------------------------------

To create a Meta Driver you just need to subclass pza_quick_server.MetaDriver

Then you have to implement 3 main functions:

- **config**: must return a configuration dict
- **setup**: to perform intitialization of the driver (run only once at startup)
- **loop**: run in loop

.. code-block:: python

    from pza_quick_server import MetaDriver

    class DriverFakeIo(MetaDriver):
        
        def config(self):
            return {
                "compatible": "fake_io",
                "info": { "type": "io", "version": "1.0" }
            }

        def setup(self, tree):
            pass

        def loop(self):
            return False


You also have special function that will help you to build your meta driver.

- **push_attribute**: to publish an attribute update

.. code-block:: python

    self.push_attribute("value", self.value, retain=True)
    # will publish the value on topic "pza/[machine]/[driver]/[interface]/atts/value"

- **register_command**: you subscribe to a command and perform an action on it.

.. code-block:: python

    def value_set(self, payload):
            print(payload)
            value_number = int(payload.decode("utf-8"))
            self.log.info("IO %s set value (%d)", self.name, value_number)
            self.value=value_number
            self.push_attribute("value", self.value, retain=True)

    def setup(self, tree):
        self.value=0
        self.register_command("value/set", self.value_set)
        # will subscribe to the topic "pza/[machine]/[driver]/[interface]/cmds/value/set"


