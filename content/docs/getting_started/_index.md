---
title: "Getting Started"
weight: 2
# bookCollapseSection: true
---

# Getting Started

This tutorial will guide you to start with panduza.

Panduza is composed of 2 main parts:

- The platform: it's the software installed into your lab that will dialog with your devices
- The clients: they are the softwares and libraries that will serve you to dialog with the platform

Currenlty the platform is only compatible with Linux systems and clients are cross-platforms.

## Platform

The goal of this first section is to install and configure the platform on your lab server.

### Installation

The installation process is easy:

**Linux**

Just execute the following command on your system, you will need admin rights.

```bash
wget -q -O - https://raw.githubusercontent.com/Panduza/panduza-installer/main/install_lastest_stable.sh | sudo bash
```

Reboot, then go to the admin interface through your web browser

```bash
localhost:8080
```

### Configuration

## Python Client

**Linux**

```bash
pip install "git+https://github.com/Panduza/panduza-py.git@main#egg=panduza&subdirectory=client/"
```

**Windows**

```bash
pip install "git+https://github.com/Panduza/panduza-py.git@main#egg=panduza&subdirectory=client/"
```


