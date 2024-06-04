---
title: "Project Overview"
weight: 2
---

This page aims to give a high-level overview of the project.

To avoid confusion, let's first define some terms:
- **Panduza**: The project as a whole.
- **Device**: A lab instrument, such as a power supply, a multimeter, etc.
- **Platform**: The [Panduza Platform](/docs/platform), a software that runs on a computer and manages the communication with the devices.
- **Libraries**: The [Panduza Libraries](/docs/libs/cpp), a set of software libraries that allow the user to interact with the platform.
- **Server**: The server is a MQTT broker. It is used to connect the platform and the libraries together.
- **Sandbox**: A graphic tool that allows the user to control and monitor the devices.
- **API**: [Application Programming Interface](https://en.wikipedia.org/wiki/API)

## Architecture overview

Panduza is an ecosystem of software components that interconnect together.

Devices are connected to a computer via any physical connection supported by the instrument (USB, Ethernet, UART etc.).\
This computer runs the Platform.

The role of the platform is to manage the internal communication with the instrument and expose its functionalities through the network.

The user can then interact with the platform through the API, using the Libraries or the *Sandbox*.

### It is important to understand that:

- Each platform can manage as many devices as you want. You define the devices you want to use in a configuration file.
- Each platform is independent from the others. You can have as many platforms as you want, and they can run on different computers.
- Every platform is a client connected to a server. This server can be local or remote, and it can be shared between multiple platforms.
- Libraries are agnostic of the platform. They connect to the server and use the API to interact with the devices.

For more information about the architecture, please refer to the [Platform](/docs/platform) and [Libraries](/docs/libs/cpp) pages.

## Technical overview

Let's dive a bit deeper into the technical details.

Panduza is based on the [MQTT](https://mqtt.org/) protocol.\
MQTT is a lightweight publish/subscribe messaging protocol designed for constrained devices and low-bandwidth, high-latency or unreliable networks.\
It is well suited for the Internet of Things.

When a Platform is configured and started, it connects to a MQTT server (called a broker).
It then subscribes to a set of topics, and publishes messages to other topics through a standard [Panduza MQTT API](/docs/mqtt).

The Libraries connect to the same MQTT server and use the same API to interact with the platform.\
When a Library connects to the broker, it subscribes to the topics it needs to receive messages from the platform, and publishes messages to the topics it needs to send messages to the platform.

In a way, the MQTT server acts as a bridge between the platform and the libraries.\
A user can only interact with the platform using the Libraries or the *Sandbox*.