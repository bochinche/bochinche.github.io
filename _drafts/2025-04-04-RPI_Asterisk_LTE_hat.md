---
layout: post
title:  "Setting Up a Standalone GSM Gateway with Raspberry Pi and Asterisk"
date:   2023-03-06 07:45:47 +0100
categories: rpi asterisk lte chan_dongle chan_quectel
---

## Introduction

This blog post describes how to set up a **standalone GSM gateway** that:

1. Can receive and make calls in a **remote location**, operating in **standalone mode**.
2. Is **easy to set up and maintain**.
3. Is **budget-friendly**, with minimal expenses beyond hardware.

---

## Hardware

- **SD Card**
- **Raspberry Pi 4B**
- **LTE Hat** (Waveshare SIM7600E-H)

---

## Software

- **Debian-based OS** for Raspberry Pi
- **Asterisk** as the VoIP Server
- Other essential **Linux utilities**

---

# Installing the OS on Raspberry Pi

## 32-bit OS

Use the official RASPIOS Lite image:
[Download RASPIOS Lite 32-bit](https://downloads.raspberrypi.org/raspios_lite_armhf/images/raspios_lite_armhf-2024-11-19/)

To ensure 32-bit mode:

```bash
vim /boot/config.txt
# or
nano /boot/config.txt
```

Add:
```bash
arm_64bit=0
```

## 64-bit OS

> ⚠️ Asterisk is **not** available in the 64-bit repository by default.

Alternative approach:
- Install a **64-bit base system**
- Add **source repositories**
- Build Asterisk **from source**

---

# Installing Asterisk and Required Modules

## Set Up the Basic System

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y build-essential libasound2-dev libsqlite3-dev autoconf automake git zsh screen vim asterisk asterisk-dev mosh libtool pkg-config
```

### Optional (but essential): Oh My Zsh

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

---

## Compiling G.729 Codecs for ARM with BCG729

> Based on "Compiling g729 codecs for ARM on Raspberry Pi B+ with bcg729"

### Compiling the BCG729 Library

```bash
mkdir -p $HOME/src
cd $HOME/src
wget http://download-mirror.savannah.gnu.org/releases/linphone/plugins/sources/bcg729-1.0.2.tar.gz
tar xzf bcg729-1.0.2.tar.gz
cd bcg729-1.0.2
./configure --libdir=/lib
make
sudo make install 
```

### Compiling G.729 Codecs

- [HowTo](http://asterisk.hosting.lv/)
- [Source Code](https://github.com/arkadijs/asterisk-g72x)

```bash
cd $HOME/src 
git clone git@github.com:arkadijs/asterisk-g72x.git 
cd asterisk-g72x 
./autogen.sh 
DESTDIR=/usr/lib/asterisk/modules ./configure --with-bcg729 
make 
sudo make install
```

### Test Modules in Asterisk

```bash
sudo systemctl restart asterisk
sudo asterisk -rvvv
asterisk*CLI> core show translation recalc 10
```

---

## Installing Channel Drivers

### Quectel & Simcom Modules

```bash
cd $HOME/src
# git clone git@github.com:IchthysMaranatha/asterisk-chan-quectel.git
cd asterisk-chan-quectel
autoupdate
./bootstrap
DESTDIR=/usr/lib/asterisk/modules ./configure --with-astversion=16.28.0
make
sudo make install
```

### `chan_dongle` for USB Modems

- [Repo](https://github.com/wdoekes/asterisk-chan-dongle/)

```bash
cd $HOME/src
git clone git@github.com:wdoekes/asterisk-chan-dongle.git
cd asterisk-chan-dongle
autoupdate
./bootstrap 
DESTDIR=/usr/lib/asterisk/modules ./configure --with-astversion=16.28.0
make 
sudo make install
```

---

## Useful Links and Resources

- [Help #253 - Timeout Issues](https://github.com/bg111/asterisk-chan-dongle/issues/253)
- [Using Quectel Voice Over UAC](https://github.com/IchthysMaranatha/asterisk-chan-quectel/discussions/2)
- [chan_dongle Timeouts](https://github.com/bg111/asterisk-chan-dongle/issues/272)
- [chan_quectel Overview](https://github.com/IchthysMaranatha/asterisk-chan-quectel)
- [Asterisk13 on Raspberry Pi](https://blog.pztop.com/2016/11/01/Asterisk13-on-RaspberryPi3/)
- [Google Voice gvsip OAuth Guide](https://community.freepbx.org/t/how-to-guide-for-creating-oauth-credentials-for-google-voice-gvsip/51187/1)
- [Asterisk with chan_dongle on Arch Linux](https://www.adeleda.com/raspberry-pi-b-with-asterisk-and-chan_dongle-on-arch-linux-en.html)

---

Happy hacking! 🚀
