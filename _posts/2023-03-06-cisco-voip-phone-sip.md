---
layout: post
title:  "Cisco VOIP Telephone with fritz.box"
date:   2023-03-06 07:45:47 +0100
categories: IT linux  
---

---
layout: post
title:  "Mirror: On Huawei 3G dongles voice capabilities"
date:   2023-04-18 08:45:47 +0100
categories: IT linux huawei dongle  
---

Good business IP phones usually come with many function keys, making our operation intuitive and easy to understand. That's why Cisco phones are popular among us. For example, I can quickly select the phone line to make outgoing calls using line keys. Also, the features for call hold, park, and transfer can be used without having to navigate through menus, and I am suitable for HD voice calls using the G.722 audio codec.

Even Cisco's former top model CP-7975G, which used to cost over 500 euros when new, is now available as a used device for 60 to 120 euros. However, almost all Cisco business phones come pre-installed with the Skinny Client Control Protocol (SCCP) only. To use me with home routers like the Fritzbox, you need to install a SIP-compatible firmware. This requires a DHCP server that convinces me to download the appropriate firmware from a TFTP server on the LAN.

We used Windows 10 as the platform for the DHCP and TFTP servers, but in principle, any operating system that has suitable servers can be used. Additionally, I require a suitable power supply at least for the flashing process because I can draw power from a switch using Power over Ethernet (PoE), but this power supply is temporarily disconnected during the flashing process, which can cause update processes to fail and damage me. Therefore, when purchasing me, make sure to also purchase a power supply as it is not included in the package.


I will show how to install a SIP-compatible firmware on a Cisco CP-7975G and a Fritzbox 6490 with FritzOS 6.83. To power the Cisco 7975G, I used the Cisco power supply CP-PWR-CUBE-3 (48 volts, 0.38A). The phone setup consists of three parts: first, setting up one or more telephony devices on the router; second, adjusting the VoIP configuration for the phone; and third, flashing the phone. The firmware upgrade and transfer of the VoIP configuration are combined in one process.

To use an IP phone with a VoIP-enabled router like the Fritzbox, there are two options: it can communicate directly with a SIP provider like Sipgate or Dus.net, or indirectly through the router's SIP server. The first option is not recommended because it disables the VoIP router's PBX and functions like in-house call forwarding or voicemail retrieval are not possible. Additionally, some VoIP routers don't forward incoming RTP packets (digitized voice signals) to clients on the LAN and instead send them to their own SIP server. Finally, a Cisco phone can easily be registered and operated on the SIP registrar of a Fritzbox.

To set up a new telephony device on the Fritzbox, I log in through the browser, open the "Telephony/Telephony Devices" menu, and click "Set up new device." I select "Telephone (with or without answering machine)," click "Next," choose "LAN/WLAN (IP phone)," and give the entry a name. A telephony device on the phone corresponds to a line, so it makes sense to name the new telephony device "Line 1," especially if you're setting up more than one. I then define the username and password. For simplicity's sake, I use "Line1" as the username. I avoid using spaces because it can cause the phones to crash. I then specify which phone number the entry should use for outgoing calls and which phone numbers it should respond to for incoming calls. I click "Apply."

If two-factor authentication is enabled on the Fritzbox, it requires confirmation, either by pressing a button on another already registered phone or by pressing one of the Fritzbox buttons. Finally, the new entry should be listed with an internal extension number. The extensions start with the number 620.

I create an entry for each phone number and note the usernames and passwords. These data will later be transferred to the phone. The 7975G can be used with up to eight SIP accounts. I save the changes and create a backup of the configuration on my PC.

With that, the Fritzbox setup is complete.

Usually, Cisco phones retrieve their IP address via DHCP at every start. Additionally, the server can instruct the phone to load files from a TFTP server via DHCP Option 66 or 150. These files can be firmware or configuration files. Although Fritz boxes contain a DHCP server, it does not support the required options for flashing. Therefore, use the free network tool TFTPD64 for Windows, which includes a DHCP and TFTP server (version 4.60 in the service edition; the portable version is not reliable on Windows 10). To prevent this specific DHCP server from confusing the clients on your LAN, create your own mini-network consisting of a PC and the Cisco phone for firmware updates. You can find all the files required for this post at ct.de/y8qf. Download all configuration files from there and install TFTPD64. Ignore the request to create firewall exceptions. They are not necessary for the mode in which this tool is used for this post.

Securing and Loading:
Cisco now offers the most important firmware versions for its business IP phones for free on the support pages. Register as a guest with your name and address to access them. Our link list at ct.de/y8qf leads to the most important firmware archives. To be prepared for all eventualities, download the voice file package "Cisco Unified Communications Locale Installer 11.5.1.3000 German (Germany)" and the latest SIP firmware 9.4(2)SR3, SIP firmware 9.3(1), and SCCP firmware 8.3(4) for the 7975G. You only need the files with the description "Firmware Files Only." Create a separate folder on your computer for each firmware and extract the firmware archives there. Copy all configuration files downloaded from the ct link, along with the empty German_Germany subfolder, into each folder. This subfolder is required for German localization. The localization is in a signed archive. If you remove the signature at the beginning of the file using a hexadecimal editor, you can extract the contents without any further ado. Install and use the Windows editor HxD for this purpose. Start the program with administrator rights and open the archive polocale-de_DE-k3-11.5.1.3000-1.cop.sgn. Under "Search/Find," select the datatype "Hex-values" and search for the character string "1F 8B 08." Select all data before this hexadecimal value, delete it by pressing the Delete key, and save the archive using "File/Save as..." with the same name but with the additional file extension .gz. Copy the contents of the path "po-locale-de_DE-k3-11.5.1.3000-1.cop.sgn.gz\po-locale-de_DE-k3-11.5.1.30001.cop.sgn\po-locale-de_DE-k3-11.5.1.3000-1.tar\usr\local\cm\tftp\german_germany" into the "German_Germany" folder. This completes the transfer of all firmware and configuration files to their destination.

Setting Up the Server:
Disconnect your PC's Ethernet cable from the Fritz box but do not connect it to the Cisco phone yet. Assign a fixed IP address to it. Use the same address currently set on the LAN side of the Fritz box. This will speed up the phone's start-up to the Fritz box later. The default is 192.168.178.1. Open "Control Panel/Network and Sharing Center/Change adapter settings" and uncheck "Internet Protocol Version 6 (TCP/IPv6)" in the properties. Open the properties for "Internet Protocol Version 4 (TCP

... work in progress...

- [CT Article 1](/assets/files/ct.17.14.136-141.pdf)
- [CT Article 2](/assets/files/ct.17.18.156-158.pdf)