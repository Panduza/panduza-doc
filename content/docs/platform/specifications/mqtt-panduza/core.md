---
title: "Interface Structure"
weight: 1
---

# Interface Structure

Each interface in Panduza has a attached MQTT Topic.

## Interface Topic

The interface MQTT topic is structured as follow:

`pza/<bench_name>/<device_name>/<interface_name>`

- *<bench_name>*: Name of the associated test bench (default by default)
- *<device_name>*: Name of the device on which the interface is attached
- *<interface_name>*: Name of the interface inside the device

### Group of Interface inside the same device

Sometime one device has multiple time the same interface.
For example, a power supply can have multiple channels so multiple BPS interfaces.

To show clients that those interfaces are organised in an array, use this notation.

```
:<array_name>_<index>:_<suffix>
```

for example

```
pza/bench/power/:channel_0:_ctrl
pza/bench/power/:channel_0:_vl
pza/bench/power/:channel_0:_am

pza/bench/power/:channel_1:_ctrl
pza/bench/power/:channel_1:_vl
pza/bench/power/:channel_1:_am
```

## Mandatory Topics

All the interfaces support those common topics.

| Topic                         |  QOS  | Retain |
| :---------------------------- | :---: | :----: |
| \<interface>/atts/info        |   0   | false  |
| \<interface>/atts/\<name> (1) |   0   |  true  |
| \<interface>/cmds/set         |   0   | false  |

(1) Interfaces may have as many \<name> attributes as they want.

## Attributes

Attributes are topics published by drivers to clients.
They serve as information that something changed or happened.

To be notified of such events, a client must subscribe to those attributes.

Each attribute have a name and some fields depending on the interface.

An attribute is represented as a JSON payload, containing its name and an object containing all the fields.

```json
{
    "attribute_name": {
        "field_1": "value",
        "field_2": 0,
        "field_3": { "sub-obj": 0, "sub-obj2": 5 }
    }
}
```

If the attribute payload has only one field, the field **must** still be present with its corresponding payload as JSON object.
**It cannot be simplified.**

```json
{
    "attribute_name": {
        "field" : "value"
    }
}
```

**Important**: An attribute payload contains all the fields supported for the specific interface.
A specific device may support only certain fields of it's generic interface attribute, In this case, other fields are not part of the payload.
- This principle allows to limit the payload to only useful information. The client API will then know what fields are supported and notify the user in case of misusage.
- If some fields are not supported, they are not part of the payload. This means the content of attribute payload may differ from one interface to another.

Example:
The PSU interface API supports a various number of settings in the attribute named settings.

Let's take the setting OVP (Over Voltage Protection) for example. Even though it is a common feature on most power supplies, one may not support it.
Therefore, the payload will vary from these power supplies. The ones that supports it will contain the field "ovp" in their settings attribute payload, and the one that doesn't won't.

This way, it is very easy for client APIs to distinguish what is allowed or not, and notify the user accordingly.

### `[PLATF_REQ_CORE_0300_00]` - Info Attribute

This attribute is special. It **must** be supported in read-only by all the interfaces and **must not** be retained.

It **must** contain:

- the type of the interface
- the version of the interface
- the state of the driver (run/error)
- An error string in case the state is error

```json
{
    "type": "serial",
    "version": "1.0",
    "state": "run",
    "error": "error string",
}
```

### Attribute Polling Cycle

Some attribute need to be monitored cyclicly by the driver. A polling cycle is the time in which each element is monitored once.

The 'polling_cycle' is an Integer. It is the number of millisecond between two read of the value.

-  0 : read as fast as possible
- -1 : disable the polling

## Commands

In order to pilot an interface, the client must send orders to the driver.

This is possible through commands.

In most cases, commands and attributes are linked entities. They act like read/write operations.
**Meaning a command always has a corresponding attribute.**

**Note: an attribute may be read-only, and therefore has no corresponding command.**

Each supported commands are united through one unique message with the following topic:

`<interface>/cmds/set`

In this topic, the user can send the commands he wants, with the fields he wants:

```json
{
    "command_1": {
        "field_1": "do the change dude !",
        "field_2": "with this setting",
        "field_3": "and why not this one too"
    },
    "command_2": "Do this other command which has only 1 field"
}
```

Since there is only one topic for all commands, **the payload can be partial**.

You can send all commands with all there fields, like in the JSON above.
You can also send only 1 command, with only 1 of its fields.

```json
{
    "command_1": {
        "field_3": "I want to change only field 3 of command 1"
    }
}
```
