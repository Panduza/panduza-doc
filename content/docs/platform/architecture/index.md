---
title: "Architecture"
description: "How the platform is organized ?"
weight: 2
---



## Meta

In the meta directory, you will find generic interface implementations.
Those implementations ease the adaptations of new device interfaces by taking care of most of the hard part of the behavior and letting to the user only the specific callback to implement.


## Log

In the log directory, you will find how traces of the application are managed.

### class

Traces in rust can take some attributes. Panduza has defined the log attribute “class” to sort event sources in the application.

