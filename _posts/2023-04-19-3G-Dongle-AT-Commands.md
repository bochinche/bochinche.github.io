---
layout: post
title:  "Huawei 3G Dongle AT Commands"
date:   2023-04-19 08:00:00 +0100
categories: IT linux huawei dongle  
---

# List of AT Commands for Huawei USB Dongle

- [List of AT Commands for Huawei USB Dongle](#list-of-at-commands-for-huawei-usb-dongle)
- [AT Commands](#at-commands)
  - [Signal Quality Report](#signal-quality-report)
- [Making a Call using AT Commands](#making-a-call-using-at-commands)
- [Links](#links)
- [Mirrors](#mirrors)

# AT Commands

|         AT Command          |                                                  Description                                                  |
| :-------------------------: | :-----------------------------------------------------------------------------------------------------------: |
|          AT+CMEE=2          |                            enable the extended error codes to get a verbose format                            |
|          AT+CPIN?           |                                      Now get the status of SIM presense                                       |
|       AT+CLCK="SC",2        |                  let us check if PIN lock feature is enabled using facility lock AT command                   |
|         AT+CFUN=1,1         |                              reset the device for SIM PIN changes to take effect                              |
|       AT+CPIN=”1234?        |                                                Unlock SIM PIN                                                 |
| AT+CPWD=”SC”,”1234?,”4321?  |                    Let us change the SIM PIN code / 1234 is current code, 4321 is new code                    |
|           AT+GSN            |                            Request International Mobile Equipment Identity (IMEI)                             |
|          AT CFUN=1          |                           Set Phone Functionality as Full (will turn on the radio)                            |
|          AT CFUN=7          |                                            will turn off the radio                                            |
|          AT QCCID           |                     Show the SIM card’s Integrated Circuit Card Identifier (ICCID) number                     |
|          AT+COPS=0          |                                         Automatic Operator selection                                          |
|          AT+COPS=?          |                Operator Status 0: Unknown / 1: Available / 2: Current operator / 3: Forbidden                 |
|           AT+CSQ            |                                             Signal quality report                                             |
|         AT^SETPORT?         |                               Displays the current configuration of the device.                               |
|       AT^GETPORTMODE        |                                 Display mode modem that is currently active.                                  |
|         AT^HSDPA=1          |                           AT^HSDPA command is used to enable/disable HSDPA support.                           |
|           AT^CLAC           |                       AT+CLAC AT command lists all AT commands supported by the mobile.                       |
|           AT+CGMI           |                        This AT command returns information about device manufacturer.                         |
|        AT+CCWA=0,0,1        |                                             disable call-waiting                                              |
|         AT+CFUN=1,1         |                                                 reboot modem                                                  |
|    AT^CARDLOCK=“<code>”     |                                               send unlock code                                                |
| AT^SYSCFG=13,0,3FFFFFFF,0,3 |                             modem 2G only, automatic search any band, no roaming                              |
| AT^SYSCFG=2,0,3FFFFFFF,2,4  |                                                      Any                                                      |
| AT^SYSCFG=13,1,3FFFFFFF,2,4 |                                                    2G only                                                    |
| AT^SYSCFG=14,2,3FFFFFFF,2,4 |                                                    3G only                                                    |
| AT^SYSCFG=2,1,3FFFFFFF,2,4  |                                                 2G preferred                                                  |
| AT^SYSCFG=2,2,3FFFFFFF,2,4  |                                                 3G preferred                                                  |
|         AT^U2DIAG=0         |                                          enable modem function only                                           |
|             ATI             |                                      get relevant information from modem                                      |
|             ATZ             |                                           reset modem configuration                                           |
|           AT+CIMI           |                                                   read IMSI                                                   |
|   AT+CLCK=“SC”,0,”<pin>”    |                                           disable PIN verification                                            |
|         AT^CVOICE=0         |                                                 enable voice                                                  |
|         AT^CVOICE=1         |                                                 disable voice                                                 |
|         AT^CVOICE=?         |                                              check voice status                                               |
|         AT^U2DIAG=0         | switch the device in modem mode only / will force the modem into serial modem mode every time it’s plugged in |
|         AT^U2DIAG=1         |                                         device in modem mode + CD-ROM                                         |
|        AT^U2DIAG=255        |                                       modem mode + CD-ROM + Card Reader                                       |
|        AT^U2DIAG=256        |                                           modem mode + Card Reader                                            |
|        AT^U2DIAG=375        |                                        will  get back into HiLink mode                                        |
|        AT+CCWA=0,0,1        |                                             disable call-waiting                                              |
|         AT+CFUN=1,1         |                                                 reset dongle                                                  |
| AT^SYSCFG=13,0,3FFFFFFF,0,3 |                                      modem 2G only, any band, no roaming                                      |

## Signal Quality Report 
Indicate the received signal strength indicator (RSSI) and the channel bit error rate (BER). For example the first received number (23) means the RSSI is -67 dBm and the second number (99) shows the channel bit error rate in percent. 0: Less than or equal to -113dBm  1: -111dBm 2…30: -109… -53dBm 31: Greater than or equal to -51dBm 99: Not known (As you see in the response from the module the status for TELUS is 2 which means it is the current operator.)

# Making a Call using AT Commands
1. AT^DDSETEX=2, which you need to issue everytime you call (because, by default, it routes the PCM data to the oblivion or the non-working mysterious PCVOICE port, dunno);
2. ATD[phonenumber]; (the semicolon is very important, trust me… Otherwise you get NO CARRIER answers)
3. AT+CHUP to hang up on the call.




# Clean SMS in SIM
| Topic                                           |    Link     |
| :---------------------------------------------1 | :---------: |
| dongle cmd dongle0 AT+CPMS=\"SM\",\"SM\",\"SM\" |             |
| dongle cmd dongle0 AT+CMGD=1,4                  |             |
| dongle ussd dongle0 *123#                       | pedir saldo |


# Links

|                  Topic                  |                                               Link                                               |
| :-------------------------------------: | :----------------------------------------------------------------------------------------------: |
|                  Speed                  |                 <https://linuxd.wordpress.com/2008/07/03/huawei-hspda-3g-modem/>                 |
|                    "                    |          <https://wiki.archlinux.org/title/Mobile_broadband_modem#Low_connection_speed>          |
|                    "                    |                       <https://bbs.archlinux.org/viewtopic.php?id=111513>                        |
|                Venezuela                |               <https://lists.ubuntu.com/archives/ubuntu-ve/2009-March/003814.html>               |
|                Venezuela                |               <https://lists.ubuntu.com/archives/ubuntu-ve/2009-March/003814.html>               |
|           General Information           |              <https://bipartisanpolicy.org/blog/cellular-data-and-digital-divide/>               |
|      The Raspberry Pi Goes Mobile       |                   <https://www.sbprojects.net/projects/raspberrypi/mobile.php>                   |
| Chapter 2: LTE-M Modem and AT Commands  |                 <https://pressbooks.bccampus.ca/cellulariot/chapter/chapter-2/>                  |
| On Huawei 3G dongles voice capabilities |                           <https://wiki.tadeu.org/misc:huaweii-voice>                            |
| Using AT Commands with the Huawei E303  |              <https://www.hologram.io/blog/using-at-commands-with-the-huawei-e303/>              |
|            AT Command Tester            | <https://m2msupport.net/m2msupport/athsdpa-athspa-athsupa-enabledisable-hsdpahspahsupa-support/> |
|          Usage of chan_dongle           |                     <http://asterisk-service.com/en_US/page/chan-dongle-use>                     |

# Mirrors
- work in progress
