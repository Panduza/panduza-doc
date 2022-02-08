
Welcome to Panduza's documentation!
=======================================

**Your Lab IoT !!!**

On embeded systems, acceptance tests are often based on stimulation of physical interfaces of the Device Under Test (DUT).

However there is a great diversity of laboratory equipements and electronic devices used to interface the test computer with the DUT. Moreover each equipement have often different communication protocols, sometimes to do the same thing.

This fact rises a problem: it's very complexe to interface all those equipements to a test framework and automate easily the acceptance tests.

Panduza aims to provide a generic API through MQTT to standardize the laboratory equipements control.

.. image:: panduza_logo.png
   :align: center



If you want to test quickly Panduza and start understanding how it works, try one of the following quick start:

.. toctree::
   :maxdepth: 1
   :caption: Quick Starts (5min)

   quick_starts/raspberry


.. toctree::
   :maxdepth: 1
   :caption: API

   api/all
   api/io
   api/serial
   api/can
   

.. toctree::
   :maxdepth: 1
   :caption: Python Client

   py_client/core
   py_client/io
   py_client/can
   

.. toctree::
   :maxdepth: 1
   :caption: Python Quick Server

   py_server/panduza_tree
   py_server/meta_driver



