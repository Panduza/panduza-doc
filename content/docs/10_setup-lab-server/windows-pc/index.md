---
title: "Windows Pc"
icon: desktop_windows
description: "Setup platform into a Windows PC"
date: 2023-08-25T23:36:29+01:00
draft: false
---

Most of electronic labs run with windows PC. Here is the page that explains how to convert it into a Panduza platform.

## Installing Mosquito MQTT Broker on Windows

Mosquito is a lightweight MQTT broker that you can use to establish a messaging infrastructure for various IoT applications. Here's a comprehensive guide to installing it on your Windows machine:

**Prerequisites:**

* A Windows computer (any version should work)
* An internet connection to download the installer

**Steps:**

1. **Download the Mosquito Installer:**

   * Head over to the official Eclipse Mosquitto website: [https://mosquitto.org/download/](https://mosquitto.org/download/)
   * Under the "Download" section, locate the appropriate installer for your Windows system (32-bit or 64-bit). It's usually a `.msi` file.
   * Download the installer and save it to a convenient location on your computer.

2. **Run the Installer:**

   * Double-click the downloaded `.msi` file to launch the Mosquito installer.
   * Follow the on-screen instructions, carefully reviewing any license agreements or configuration options.
   * It's recommended to keep the default installation path (`C:\mosquitto`).

3. **Start the Mosquito Broker Service:**

   * Once the installation is complete, you'll have the option to launch the Mosquito broker service immediately. If you didn't choose that option, you can start it manually:
     * Press the Windows key + R to open the Run dialog.
     * Type `services.msc` and press Enter to open the Services window.
     * Locate the "Mosquitto Broker" service in the list.
     * Right-click on the service and select "Start" to begin the MQTT broker.

**Verification:**

* To confirm that Mosquito is running, you can use an MQTT client to connect to the broker. Here are a couple of popular options:
   * **MQTTfx** (cross-platform desktop client): [https://mosquitto.org/download/](https://mosquitto.org/download/)
   * **MQTTLens** (web-based client): [https://chrome.google.com/webstore/detail/mqttbox/kaajoficamnjijhkeomgfljpicifbkaf](https://chrome.google.com/webstore/detail/mqttbox/kaajoficamnjijhkeomgfljpicifbkaf)
* Use the following connection details in your MQTT client:
   * **Broker address:** `localhost` (or your machine's IP address if connecting from another device)
   * **Port:** `1883` (the default port for MQTT)

**Additional Notes:**

* If you encounter any issues during installation or configuration, refer to the official Mosquito documentation for troubleshooting steps: [https://mosquitto.org/documentation/](https://mosquitto.org/documentation/)
* Consider firewall settings if you're connecting from a different device on your network. You might need to allow incoming connections
*  on port 1883.

## Install the platform 

test
