---
title: "Platform"
weight: 100
bookCollapseSection: true
---

# Platform Guide

As describes in the [Architecture overview](/docs/introduction/project_overview#architecture-overview), the platform is the client software that manages the communication with the devices.

## Configuration

### Manual configuration

In order to know what devices are connected to the platform and where the server is located, the platform needs to be configured through a configuration file called the **tree**.
This file is written in JSON format and describes:
- The server IP address
- The server port
- The list of devices connected to the platform

Here is an example of a tree file:
```JSON
{
    "devices": [
        {
            "model": "Panduza.FakePsu",
            "settings": {
                "number_of_channel": 1
            }
        },
        {
            "model": "Panduza.FakeDioController",
            "settings": {
                "number_of_dio": 2
            }
        }
    ]
}
```

Providing an IP address and a port is optional. If no server is provided, the platform will connect to `localhost` on port `1883`.

If no tree is provided, the platform will search for the tree file in the following locations:
- Linux: `/etc/panduza/tree.json`
- Windows: TODO

TODO: Broker tree?

### Automatic discovery

TODO: (hunt)

## Devices

Devices are grouped into [families](/docs/supported_devices/#devices-families).\
Each device described in the **tree** represents a physical instrument connected to the platform.

### Model

- `model` field is used to identify the device and must always match a device's [driver](/docs/platform/#drivers).

The desired naming convention for the model name is `<Manufacturer>.<Model>`.\

This is not mandatory but it is recommended to avoid conflicts between devices and to make it easier to identify the device.


### Settings

- `settings` field is used to configure the device settings.

The settings are specific to each device and are described in the [device's family page](/docs/supported_devices/#drivers).
A family will contain a list of generic settings that are usually common to all devices of the same family.


It is possible that a device has specific settings that are not described in the family page.\
In this case, the device's table section lists all the extra settings available for this device.



It might also happen that a device does not support a family generic setting.\
In this case, the setting will be ignored and a warning will be displayed in the logs.


### Fake devices

Sometimes it is useful to have a virtual device for testing purposes.\
For this reason, the platform provides a fake device for each family.

This is particularly useful when developing new tests and checking that your application behaves as expected without requiring a real hardware device.


For example, you can simulate a power supply with a fake device and check how other part of your application react to it.\
Imagine having a test where, depending on the power supply voltage, another part of your application is expected to behave in a certain way.

With a fake device, you can easily test all the different scenarios.\
The moment you will have a real power supply, you will be able to run the same test and check that the behavior is the same, by simply changing the model name in the tree file.



Although fake devices are quite handy for testing and development purposes, they are not meant to be used in production.\
You should always use a real device when running hardware-in-the-loop tests.


## Drivers

### Device drivers

To talk to a device, the platform needs to know how to communicate with it.\
This is done through a device driver.

A driver is usually a collection of callbacks that are used to send commands to the device and to receive data from it.\
Each driver is derived from a [Meta Driver](/docs/platform/#meta-drivers).


When two devices share the exact same functionalities and communication protocol, they can share the same driver.\
In order to avoid code duplication, the platform allows to define a driver that can be used by multiple devices.\
This is done through a `compatible` field in the driver definition.


### Meta drivers

Meta drivers are used to define the common interface for all drivers of the same family.\
They are used to define the common settings and interfaces for all devices of the same family.


For example, all power supplies drivers are derived from the `MetaDriverPsu` driver.\
This driver defines the common settings and interfaces for all power supplies.


## Connectors

AG_PROPOSAL: Je dis surement nimp dans cette section, c'est pas clair du tout dans ma tete.


Devices communicate back and forth with the platform through a certain communication protocol.\
Whether it is a serial port, a TCP/IP connection, a USB port, etc. the platform needs to know how to communicate with the device.

Drivers usually define the communication protocol to use, since it is specific to each device.\
To do so, it uses a connector.

Connectors have two main purposes:
- Provide generic and reusable read and write operations for a communication protocol
- Provide a way to handle multiple communication protocols for a single device

Most of the time, devices have only one communication protocol.\
However, it can happen that a device supports multiple ways to communicate with it.

For example, some power supplies can be connected to a computer through a serial port or through an Ethernet port.

A connector has a list of settings that are specific to the communication protocol it uses.


For example, a serial port connector will have a `port` setting to specify the serial port to use.
A TCP/IP connector will have `ip` and `port` settings.



When that happens, the driver will define two connectors: one for the serial port and one for the Ethernet port.\
The platform will try to automatically detect which connector to use.\
This behavior can be overridden by specifying the `connector` to use in the tree file.


### List of supported connectors

#### TTY Serial port

| Name | Description |
| --- | --- |
| `serial_tty` | TTY Serial port |

| Settings | Type | Default | Description |
| --- | --- | --- | --- |
| `port_name` | `port` | `string` | `/dev/ttyUSB0` | Serial port to use |
|`baudrate` | `int` | `9600` | Serial port baudrate |
|`bytesize` | `int` | `8` | Serial port bytesize |
|`parity` | `string` | `none` | Serial port parity |
|`stopbits` | `int` | `1` | Serial port stop bits |
| `rtscts` | `bool` | `false` | Serial port RTS/CTS flow control |
| `timeout` | `int` | `1000` | Serial port timeout in milliseconds |
| `write_timeout` | `int` | `1000` | Serial port write timeout in milliseconds |

## Services

TODO


AG PROPOSAL: Software services, same level as devices.
Used for example to connect to a database, or to a web server, or to a file system, etc.
Example: SSH

Why not using connectors for that? Because connectors are meant to be used to connect to a device, not to a service.\
Why not a device? Because a device is meant to be a physical instrument
