---
title: "Attribute Types"
weight: 100
description: ""
icon: cloud
---

### `[PLATF_00018]` - Attribute A0

Historic attribute type for Panduza.

- Commands sent on topic "cmds/set"
- Acknowledge on reading the topic "atts/{att_name}"

Payloads: json

Its main goal was to be able to set multiple attributes with the same command. It supported only a "control" vision of Panduza.
This type should be avoided for new interfaces.

### `[PLATF_00019]` - Attribute A1

Attributes for field control

Similar to A0 but with a dedicated cmds topic

- Commands sent on topic "cmds/{att_name}"
- Acknowledge on reading the topic "atts/{att_name}"

Payloads: json

atts topic: retained true !

cmds and atts are mirroring, to set a value just send it into cmds and atts will reflect if accepted.

Some fields or all felds can be ReadOnly.

### `[PLATF_00020]` - Attribute A2

free cmds (send command on the custom format defined by the interface)

### `[PLATF_00020]` - Attribute A3

free atts (value returned on the custom format defined by the interface)

atts topic: retained true !
