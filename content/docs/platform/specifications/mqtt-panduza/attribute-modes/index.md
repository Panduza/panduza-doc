---
title: "Attribute Modes"
weight: 100
description: "Each attribute must declare a mode defining how it will interact with MQTT"
icon: cloud
---


3 modes:

- M1: Control (set value and ensure the platform applied it)
- M2: Push Stream (send huge amount of data to the platform in a stream)
- M3: Pull Stream (receive huge amount of data from the platform in a stream)




## Performance Benchmarks

- C - CLIENT
- B - BROKER
- P - PLATFORM 

- LCB: Latency between Client and Broker
- LBP: Latency between Broker and Platform 

- N - NUMBER OF ITERATIONS 
- S - PAYLOAD SIZE


