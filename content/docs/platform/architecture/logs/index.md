---
title: "Logs"
description: "Logs Organisation"
weight: 10
icon: "analytics"
---

## Log Events

Log events are organized in class and items.

Each class and item must have a name if used.

items are optional.

There is 3 item max.

Examples:

- class=Platform / i1=Services
- class=Interface / i1=default / i2=device / i3=my_interface


## Formaters

### Github formatter

The goal of this formatter is to provide to the user a Github issue that he can copy/past on Github to report an issue.

It produces a brief in markdown with main versioning informations and a csv file with complete log for later analysis.

- timestamp
- Level (debug/info/warning...)
- class
- i1
- i2
- i3
- message
- thread/task
