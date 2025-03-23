---
layout: post
title:  "Easily Connecting My Raspberry Pi to the Internet Using a Waveshare SIM7600E-H 4G HAT"
date:   2025-03-23 08:00:00 +0100
categories: linux rpi LTE gsm 4G
---


## 📡 How I Easily Connected My Raspberry Pi to the Internet Using a Waveshare SIM7600E-H 4G HAT

Getting your Raspberry Pi online using a 4G HAT might sound complicated — but with the **Waveshare SIM7600E-H 4G HAT**, it turned out to be surprisingly simple. In this post, I’ll walk you through my quick setup and share some helpful links and tools I used along the way.

---

### 🔧 What You Need

- A Raspberry Pi (I used a Pi 4 with Raspberry Pi OS Bookworm Lite)
- Waveshare **SIM7600E-H 4G HAT**  
  👉 [Official Wiki](https://www.waveshare.com/wiki/SIM7600E-H_4G_HAT)
- SIM card with mobile data
- USB connection from HAT to Pi (the USB port is used for networking, not the serial GPIOs)
- Some patience (but not too much 😄)

---

### ⚡️ Step 1: Attach and Power the 4G HAT

1. Insert your **SIM card** into the slot on the HAT.
2. Connect the **main and auxiliary antennas**.
3. Plug the **USB cable** from the HAT to your Pi.
4. Use the **GPIO 5V headers** or USB to power the module.
5. Wait for the **NET LED** to start blinking regularly (meaning it's registered on the network).

---

### 🌐 Step 2: Let Linux Recognize the Device

Boot up your Pi and check if the device is recognized. Run:

```bash
lsusb
```

You should see something like:

```
Bus 001 Device 004: ID 2c7c:0125 Quectel Wireless Solutions Co., Ltd.
```

If that appears, you’re good to go. The HAT acts like a USB modem/NIC.

---

### 🧙‍♂️ Step 3: Use `nmcli` to Connect

The easiest way to establish a mobile connection is with `nmcli` (NetworkManager CLI). I followed the exact steps described in this helpful blog post:  
👉 [WimsWorld - SIM7600G-H on Bookworm](https://wimsworld.wordpress.com/2023/12/21/revisiting-the-sim7600g-h-4g-hat-using-bookworm/)

#### Enable the modem interface:

```bash
sudo nmcli device
```

Look for something like `wwan0` or `cdc-wdm0`.

#### Create a connection:

```bash
sudo nmcli connection add type gsm ifname "*" con-name "4G" apn internet
```

*Note: Replace `"internet"` with your carrier's APN if different.*

#### Bring up the connection:

```bash
sudo nmcli connection up "4G"
```

And that’s it — your Pi is now online via mobile data! 🎉

---

### 🛠 Troubleshooting Tips

- If `nmcli` complains about the device being locked, try:

```bash
sudo mmcli -m 0 --unlock
```

- No device showing up in `nmcli`? Try:

```bash
sudo apt install usb-modeswitch modemmanager
```

- To monitor interfaces:

```bash
ip link show
```

- For auto-reconnect setups and deeper wvdial usage:  
  👉 [This Medium Guide is Gold](https://medium.com/@naveenkumarasinghe/auto-connecting-usb-modems-on-linux-raspberry-pi-with-wvdial-daemon-90db240916de)

---

### 🧵 Resources That Helped Me

- 📘 [Waveshare SIM7600E-H Wiki](https://www.waveshare.com/wiki/SIM7600E-H_4G_HAT)
- 🧪 [Raspberry Pi Forums - USB Modem Threads](https://forums.raspberrypi.com/viewtopic.php?t=238594)
- 🧰 [nmcli usage examples](https://networkmanager.dev/docs/api/latest/nmcli-examples.html)
- 🔍 [List interfaces in Linux](https://www.cyberciti.biz/faq/linux-list-network-interfaces-names-command/)
- 💾 [Headless Raspberry Pi setup](https://www.raspberrypi.com/documentation/computers/configuration.html#setting-up-a-headless-raspberry-pi)
- 📞 [SIMCom Official Site](https://www.simcom.com/)

---

### 🚀 Final Thoughts

The Waveshare SIM7600E-H HAT has proven to be a solid and reliable way to get mobile internet on a Raspberry Pi. It’s plug-and-play if you're using NetworkManager — and once set up, it can run headless in remote setups, perfect for IoT or field deployments.

Let me know if you’re using a different HAT or want to auto-start the connection on boot. Happy hacking! 💻📶
