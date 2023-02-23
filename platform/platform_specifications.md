# Platform Specifications

A panduza platform must repesct the following requirements




## [26CA-00] Tree.json

Platform must get its configuration from the file tree.json


## [53B7-00] Interfaces Bootup Order

Platform must boot interfaces in the following order:

- For each broker declared in the *tree.json*: create a MQTT client, attach it to a thread and test the connection
- For each interface declared in the *tree.json*: create its driver instance, attach it to a MQTT client and to a thread
- For each driver instance created: start the driver


## [48A9-00] One thread for each client


## [48A9-00] Client can manage multiple interface


## [48A9-00] Thread can manage multiple interface

by default all the interfaces must share to same thread

## [48A9-00] Platform special interface

The platform must manage a special interface of type *platform* for each managed broker (broker declared in the *tree.json*)




