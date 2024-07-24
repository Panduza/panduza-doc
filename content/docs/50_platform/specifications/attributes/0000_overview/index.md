---
title: "Overview"
description: "How attributes are organized ?"
weight: 0000
icon: grid_view
---


Attribute == topic + CMDS/ATTS channel

Stream Attribute == topic + RX/TX channel on stream broker (QUIC + ?)
Message Attribute == topic + RX/TX channel on message broker (TCP/TLS + MQTT)


# Message Attributes

Basic => only a value with a simple type

- Attribute Boolean => payload 0 => false, 1 => true
- Attribute String => 
- Attribute Numeric => String avec nombre potentiellement en decimal

# Stream  Attributes

Monitoring Stream => from device to user (only ATTS)
Command Stream => from user to device (only CMDS)


