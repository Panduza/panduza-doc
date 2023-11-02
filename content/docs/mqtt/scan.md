---
title: "Scan Mechanism"
weight: 1
---

# Scan Mechanism

Panduza provides a scan mechanism to discover which device and interfaces are up on a given broker.

Most of this mechanism works with the topic 'pza'.

### `[REQ_SCAN_0001]` - Scan all interfaces

When '*' is published inside the topic 'pza' then each interface working on the broker **must** publish their info attribute.

### `[REQ_SCAN_0002]` - Scan platform interfaces only

When 'p' is published inside the topic 'pza' then each interface working on the broker **must** publish their info attribute if the interface has type == platform.

### `[REQ_SCAN_0003]` - Scan device interfaces only

When 'd' is published inside the topic 'pza' then each interface working on the broker **must** publish their info attribute if the interface has type == device.

### `[REQ_SCAN_0004]` - Scan all interfaces of a given device

When '<bench_name>/<device_name>' is published inside the topic 'pza' then each interface working on the broker **must** publish their info attribute if the interface base topic is the device base topic (to be accurate the 'device' interface will respond too).

