---
title: "Basis"
description: "-"
weight: 0000
icon: grid_view
---

## Protocols

Panduza is based on PUB/SUB protocols.

- MQTT/TCP: For most communication
- Custom/QUIC: For stream communication

## Topics

Panduza topics are structured as follow:

```
<N>/pza/<P>/<D>/<I0>/.../<In>/<A>/<S>
```

- N: Namespace Identifier: it is a topic defined by the user to isolate its platforms on the broker.
- P: Platform Identifier: name of the platform supporting devices.
- D: Device Identifier: name of the device
- I0...In: Interface Identifiers: n level of interfaces are possible to group attributes
- A: Attribute Identifier: name of the attribute
- S: specifier [cmd|att] cmd to send data to attribute, att the get state of the attribute


## Scan

A client can scan a given namespace by:

- subscribing to `<N>/pza/+`
- then sending `*` in topic `<N>/pza`

All the platform no the namespace will respond on their platform topic.

The platform topic is only usefull for the scan

```
<N>/pza/<P>
```

It gives the path of the interface that manage the platform:

Proposition:

```
<N>/pza/<P>/_/_
```

## Platform interface

Attributes:

```
examples 

<N>/pza/<P>/_/_/structure/att

<N>/pza/<P>/_/_/devices_states/att

<N>/pza/<P>/_/_/dtree/att
<N>/pza/<P>/_/_/dtree/cmd
```

- structure (json/protobuf attribute)
    - The tree structure of devices managed by this platform: 
        - name of devices
        - name of interfaces inside devices or inside others interfaces
        - name, type and constantes fields of attributes
    - Change only if structure change



- devices_states (json/protobuf attribute)
    - The state of each device and cause of the error if state error
    - Change only if state of a device change

- dtree  (json attribute)
    - content of the device tree, allow use to change the configuration

- store (json/protobuf attribute)

- hunt ?
