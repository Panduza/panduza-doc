---
title: "Architecture"
description: "How the platform is organized ?"
weight: 2
---

The platform sources are coded in Rust and are organized by directory reflecting its architecture.

## builtin_devices

This directory contains devices and interface implementations that come built-in the main platform sources.

In this directory there must be one directory for each manufacturer. The manufacturer directory must hold devices related to its produc
ts.

## Meta

In the meta directory, you will find generic interface implementations.
Those implementations ease the adaptations of new device interfaces by taking care of most of the hard part of the behavior and letting to the user only the specific callback to implement.


## Log

In the log directory, you will find how traces of the application are managed.

### class

Traces in rust can take some attributes. Panduza has defined the log attribute “class” to sort event sources in the application.

