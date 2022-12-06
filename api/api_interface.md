# Interface Structure

## Attributes

An interface is composed of attributes.

Each attribute have a name and some fields.

An attribute can be written as a json.

```json
{
    "attribute_name": {
        "field_1": "value",
        "field_2": 0,
        "field_3": { "sub-obj": 0, "sub-obj2": 5 }
    }
}
```

If the attribute payload is not an object json, for example

```json
{
    "attribute_name": "hello"
}
```

Then the payload is supposed to be attached to the field called "value" if any.

## Topics

All the interfaces support those common topics

| Topic                                    | QOS | Retain |
| :--------------------------------------- | :-: | :----: |
| {INTERFACE_PREFIX}/atts/info             |  0  | false  |
| {INTERFACE_PREFIX}/atts/{ATTRIBUTE_NAME} |  0  |  true  |
| {INTERFACE_PREFIX}/cmds/set              |  0  | false  |


### {INTERFACE_PREFIX}/atts/{ATTRIBUTE_NAME}

This topic contains the json representation of the attribute called {ATTRIBUTE_NAME}.

### {INTERFACE_PREFIX}/cmds/set

This topic allow the user to change attributes.

In this topic, the user can send multiple attribute change:

```json
{
    "attribute_1": {
        "field_1": "do the change dude !",
    },
    "attribute_2": 42
}
```

### Special attribute 'info'

This attribute is special and must be supported in read-only by all the interfaces.

It is special because it must not be retained.

When '*' is published inside the topic 'pza' then this attribute must be published




