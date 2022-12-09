# Interface Structure

## Topics

All the interfaces support those common topics.

| Topic                         |  QOS  | Retain |
| :---------------------------- | :---: | :----: |
| \<interface>/atts/info        |   0   | false  |
| \<interface>/atts/misc        |   0   |  true  |
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

### Info Attribute

This attribute is special. It must be supported in read-only by all the interfaces and **must not be retained**.

When '*' is published inside the topic 'pza' then this attribute must be published.

It contains the type of the interface, and the version of the meta driver.

```json
{
    "type": "serial",
    "version": "1.0"
}
```

### Misc Attribute

This attribute is used to gather all miscellaneous information. Any interface API can specify their own misc payload content.

This misc attribute contains only fields that cannot be considered specific to an interface family.

For example, a serial port or a polling timing might be useful for the power supply interface, but they don't describe a specific attribute of power supplies.

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
