---
layout: post
title:  "Huawei 3G Dongle AT Commands"
date:   2024-04-18 07:45:47 +0100
categories: IT linux huawei dongle  
---

# List of AT Commands for Huawei USB Dongle

- [List of AT Commands for Huawei USB Dongle](#list-of-at-commands-for-huawei-usb-dongle)
- [AT Commands](#at-commands)
  - [Signal Quality Report](#signal-quality-report)
- [Links](#links)


# AT Commands
|         AT Command         |                                  Description                                   |
| :------------------------: | :----------------------------------------------------------------------------: |
|         AT+CMEE=2          |            enable the extended error codes to get a verbose format             |
|          AT+CPIN?          |                       Now get the status of SIM presense                       |
|       AT+CLCK="SC",2       |   let us check if PIN lock feature is enabled using facility lock AT command   |
|        AT+CFUN=1,1         |              reset the device for SIM PIN changes to take effect               |
|       AT+CPIN=”1234?       |                                 Unlock SIM PIN                                 |
| AT+CPWD=”SC”,”1234?,”4321? |    Let us change the SIM PIN code / 1234 is current code, 4321 is new code     |
|           AT+GSN           |             Request International Mobile Equipment Identity (IMEI)             |
|         AT CFUN=1          |            Set Phone Functionality as Full (will turn on the radio)            |
|         AT CFUN=7          |                            will turn off the radio                             |
|          AT QCCID          |     Show the SIM card’s Integrated Circuit Card Identifier (ICCID) number      |
|         AT+COPS=0          |                          Automatic Operator selection                          |
|         AT+COPS=?          | Operator Status 0: Unknown / 1: Available / 2: Current operator / 3: Forbidden |
|           AT+CSQ           |                             Signal quality report                              |
|        AT^U2DIAG=0         |     will force the modem into serial modem mode every time it’s plugged in     |
|       AT^U2DIAG=375        |                        will  get back into HiLink mode                         |
|        AT^SETPORT?         |               Displays the current configuration of the device.                |
|       AT^GETPORTMODE       |                  Display mode modem that is currently active.                  |
|         AT^HSDPA=1         |           AT^HSDPA command is used to enable/disable HSDPA support.            |
|          AT^CLAC           |       AT+CLAC AT command lists all AT commands supported by the mobile.        |
|          AT+CGMI           |         This AT command returns information about device manufacturer.         |

 ## Signal Quality Report 
Indicate the received signal strength indicator (RSSI) and the channel bit error rate (BER). For example the first received number (23) means the RSSI is -67 dBm and the second number (99) shows the channel bit error rate in percent. 0: Less than or equal to -113dBm  1: -111dBm 2…30: -109… -53dBm 31: Greater than or equal to -51dBm 99: Not known (As you see in the response from the module the status for TELUS is 2 which means it is the current operator.)

# Links
|                  Topic                  |                                     Link                                     |
| :-------------------------------------: | :--------------------------------------------------------------------------: |
|                  Speed                  |        https://linuxd.wordpress.com/2008/07/03/huawei-hspda-3g-modem/        |
|                    "                    | https://wiki.archlinux.org/title/Mobile_broadband_modem#Low_connection_speed |
|                    "                    |              https://bbs.archlinux.org/viewtopic.php?id=111513               |
|                Venezuela                |      https://lists.ubuntu.com/archives/ubuntu-ve/2009-March/003814.html      |
|                Venezuela                |      https://lists.ubuntu.com/archives/ubuntu-ve/2009-March/003814.html      |
|           General Information           |     https://bipartisanpolicy.org/blog/cellular-data-and-digital-divide/      |
|   The Raspberry Pi Goes Mobile  |          https://www.sbprojects.net/projects/raspberrypi/mobile.php          |
| Chapter 2: LTE-M Modem and AT Commands |        https://pressbooks.bccampus.ca/cellulariot/chapter/chapter-2/         |
| On Huawei 3G dongles voice capabilities |                  https://wiki.tadeu.org/misc:huaweii-voice                   |
| Using AT Commands with the Huawei E303  |     https://www.hologram.io/blog/using-at-commands-with-the-huawei-e303/     |
| AT Command Tester | https://m2msupport.net/m2msupport/athsdpa-athspa-athsupa-enabledisable-hsdpahspahsupa-support/ |


# Mirrors