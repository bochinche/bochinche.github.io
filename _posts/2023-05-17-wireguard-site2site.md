---
layout: post
title:  "Wireguard: site to site (lan 2 lan) between linux and fritz.box"
date:   2023-05-17 17:45:47 +0100
categories: IT Germany 
---

## Introduction:
With the introduction of WireGuard and Fritz.OS 7.50, you can replace your IKEv1 site-to-site LAN tunnel with a more efficient and secure solution. This guide will walk you through the process of configuring a WireGuard tunnel between a Linux-based Virtual Private Server (VPS) and a Fritz.Box server in your home LAN.

## Prerequisites:
WireGuard package successfully installed on both the Linux server and Fritz.Box (Fritz.OS >= 7.50).
Basic understanding of networking concepts and command-line usage.

1. Generate Key Pairs:
Run the following commands to generate two private and public key pairs on your Linux server (alpha site) and save them to respective files:

```bash
wg genkey | sudo tee /etc/wireguard/wgA.key
sudo cat /etc/wireguard/wgA.key | wg pubkey | sudo tee /etc/wireguard/wgA.pub
wg genkey | sudo tee /etc/wireguard/wgB.key
sudo cat /etc/wireguard/wgB.key | wg pubkey | sudo tee /etc/wireguard/wgB.pub
```

2. Update Configuration Files:
Edit the following configuration files, replacing the placeholders with your network topology and generated keys.

Linux Server Configuration (alpha site):
File: /etc/wireguard/wgA.conf

```bash
[Interface]
Address = 10.10.9.1/24
ListenPort = 51820
PrivateKey = <PRIVATE_KEY_A>

[Peer]
PublicKey = <PUBLIC_KEY_B>
AllowedIPs = 10.10.9.2/32, 10.10.11.0/24
```

Fritz.Box Configuration (beta site):
File: /etc/wireguard/wgB.conf (to be imported over the Fritz.Box web interface)

```bash
[Interface]
PrivateKey = <PRIVATE_KEY_B>
ListenPort = 51820
Address = 192.168.150.1/24

[Peer]
PublicKey = <PUBLIC_KEY_A>
AllowedIPs = 10.10.9.0/24, 10.10.10.0/24
Endpoint = <IP_ADDRESS_A>:51820 (replace with your Linux server's external IP address)
PersistentKeepalive = 25
```

3. Apply the configuration
- On the linux server
```bash
sudo systemctl enable --now wg-quick@wgA
```
- On the Fritz.Box 
Import using the wireguard import dialoge for lan-2-lan tunnels. The following images are for reference
![image](/assets/images/fritz.box-1.png)
![image](/assets/images/fritz.box-2.png)
![image](/assets/images/fritz.box-3.png)

4. Network Topology (refenrence) 
There are two sites:
- alpha site is a linux server with a persisten DNS address. In this example we will assume that the external IP address of the linux server is **8.8.3.3**
- beta site is a fritz.box server with a dynamic (non-persisten DNS) 


                  ┌─────── WireGuard tunnel ──────┐
                  │         10.10.9.0/31          │
                  │                               │
     10.10.9.0 wgA│               xx              │wgB 10.10.9.1
                ┌─┴─┐          xxx  xxxx        ┌─┴─┐
alpha site      │   │ext     xx        xx    ext│   │  beta site (fritz.box)
                │   ├───    x           x    ───┤   │
10.10.10.0/24   │   │      xx           xx      │   │  10.10.11.0/24
                │   │      x             x      │   │
                └─┬─┘      x              x     └─┬─┘
        10.10.10.1│        xx             x       │10.10.11.1
...┌─────────┬────┘          xx   xxx    xx       └───┬─────────┐...
   │         │                  xx   xxxxx            │         │
   │         │                                        │         │
 ┌─┴─┐     ┌─┴─┐           public internet          ┌─┴─┐     ┌─┴─┐
 │   │     │   │                                    │   │     │   │
 └───┘     └───┘                                    └───┘     └───┘

# Links 
- [https://administrator.de/forum/s2s-wireguard-avm-zu-mikrotik-4495761391.html#comment-6874546842](https://administrator.de/forum/s2s-wireguard-avm-zu-mikrotik-4495761391.html#comment-6874546842)
- [https://administrator.de/forum/wireguard-lan-to-lan-fritzbox-raspberry-pi-5100109633.html](https://administrator.de/forum/wireguard-lan-to-lan-fritzbox-raspberry-pi-5100109633.html)
- [https://schroederdennis.de/allgemein/wireguard-site-to-site-vpn-zwei-netzwerke-sicher-verbinden/](https://schroederdennis.de/allgemein/wireguard-site-to-site-vpn-zwei-netzwerke-sicher-verbinden/)
- [https://avm.de/service/vpn/wireguard-vpn-zwischen-fritzbox-und-anderem-router-einrichten/dok2/3687_WireGuard-VPN-zwischen-FRITZ-Box-und-anderem-Router-einrichten/](https://avm.de/service/vpn/wireguard-vpn-zwischen-fritzbox-und-anderem-router-einrichten/dok2/3687_WireGuard-VPN-zwischen-FRITZ-Box-und-anderem-Router-einrichten/)
- [https://ubuntu.com/server/docs/wireguard-vpn-site2site](https://ubuntu.com/server/docs/wireguard-vpn-site2site)
- [https://www.ivpn.net/knowledgebase/linux/linux-autostart-wireguard-in-systemd/](https://www.ivpn.net/knowledgebase/linux/linux-autostart-wireguard-in-systemd/)