---
title: "Performance Tests"
weight: 10
icon: star
---

The perf test is located in the platform test repository

- https://github.com/Panduza/panduza-platform-tests-core

It is located in scripts/perf_test.py

When you start it, it will search on the broker for a "ping" interface.

You can generate a ping interface on your platform with the given tree:

```json
{
    "devices": [
        {
            "name": "test_device",
            "ref": "panduza.test"
        }
    ]
}
```

Once the ping interface found, the test will send payload to the ping interface and wait for answers, computing the speed of the connection.
