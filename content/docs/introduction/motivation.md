---
title: "Motivation"
weight: 1
---

# Motivation

Embedded systems are everywhere and are only getting more complex.

But still today, the tools we use to develop them are stuck in the past.\
We have great IDEs, debuggers, lab instruments, and simulators, but they don't work well together.

During the lifespan of any project, we encounter a multitude of challenges:

## Hardware-in-the-loop testing

*It works in simulation...*\
Great! But does it work in the **real world**?

**Hardware-in-the-loop** is a powerful technique for testing embedded systems in a realistic environment.\
But not only test benches are often difficult to set up and use, they are also expensive, which can limit there accessibility for many teams.

## Diverse lab equipment

There are almost as many lab instruments as there are protocols for controlling them.\
Each piece of equipment has its unique protocol and interface, which can complicate the setup of a functional test environment.

## Remote operations

With the rise of remote work and distributed teams, it's increasingly important to enable remote operation of hardware setups.

## Glue code

Whether it's a test setup or a development environment, there's often a lot of glue code involved in getting everything to work together.\
This glue code is often non-reusable, which can lead to wasted time and effort when a new project comes along.

## Software tools cost

Most of software tools for embedded systems engineers are expensive and proprietary.\
This can be a barrier to entry for many teams, especially those with limited budgets.

## Cross-platform compatibility

As Linux becomes more commonly used as a development platform for embedded systems, there's a growing need for cross-platform tools.\
No Linux user wants a dual boot or a virtual machine just to run a piece of software.\
Yet, most of hardware engineers use Windows, and the two worlds must coexist in harmony.

## So...

Embedded system development is hard.

It's hard to develop, hard to test, and hard to debug.

It's hard to develop because it's hard to test and debug.\
It's hard to test because it's hard to debug and develop.\
It's hard to debug because it's hard to develop and test.

It's a vicious cycle.

**But we love it, so let's make it better.**

**Panduza** provides a solution to these problems:

## Standardized device API

Two devices may have the same features but very different ways to be addressed.\
With Panduza, all the devices from a same family will be accessible via universal interfaces.\
Supporting new equipment is a few lines of code away.

## Flexible setups

As many instruments as you want, as many computers as you want, all connected together through a single API.\
From a Raspberry Pi to a supercomputer, Panduza can run on any system and you can access your test environment remotely from anywhere in the world.

Windows or Linux, use whatever you want.

## Reusable code

Code libraries with standard interfaces for each type of instrument allow you to reuse your code across projects.\
If your tests depend on a specific piece of equipment, you can easily swap it out for another one.\
No need to rewrite your code. If the functionalies you need are the same between the two instruments, your code will work as is.

## Graphic tools

Panduza provides a set of graphic tools to control and monitor your test environment.\
If you don't want to write code, you don't have to.

## Cost-effective

Panduza is **free and open-source**, and **will always be**.