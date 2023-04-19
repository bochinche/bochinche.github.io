---
layout: post
title:  "Mirror: On Huawei 3G dongles voice capabilities"
date:   2023-04-18 08:45:47 +0100
categories: IT linux huawei dongle  
---

This is Google's cache of [https://wiki.tadeu.org/misc:huaweii-voice](https://wiki.tadeu.org/misc:huaweii-voice). It is a snapshot of the page as it appeared on 4 Apr 2023 23:43:48 GMT. The [current page](https://wiki.tadeu.org/misc:huaweii-voice) could have changed in the meantime. [Learn more.]

# Table of Contents

*   [On Huawei 3G dongles voice capabilities](#On Huawei 3G dongles voice capabilities)
    
    *   [On locked/unlocked voice function](#On locked/unlocked voice function)
        
    *   [How it works](#How it works)
        
    *   [In practice](#In practice)
        
    *   [References](#References)
        

# On Huawei 3G dongles voice capabilities

Maybe I'm coming late to the party, but I do have a 3G UMTS modem from Huawei – the E303C. It has a lot in common with other devices, though, like E173 or E220. It's worth mentioning that's the barebones version, so there's no HiLink non-sense. It comunicates through serial ports, not per via RNDIS (_grosso modo_, emulated ethernet). Works fine both on Linux or Windows and you don't really need to install the Huawei Partner thing. But I won't go into detail on that, now. Suffice to know that once it's exposing it's serial ports to the host, the system can comunicate with it as it were an old fashioned hardware (no WinModems here!) dialup modem (which it indeed is, sort of).

But there's a nifty feature to the Partner software: a dialer. That is: if you dongle came with unlocked voice function **and** the operator enabled it on it's Partner software's distribution. Mine came unlocked voice, but no calling function on the Partner software. Doesn't matter. I just used one from India, I think? Or was it Vodafone? I don't remember. But I got voice.

Okay, so you may want to use voice on Linux **and** without using the Partner software (whose Linux version seems to be crappy). Well, you're out of luck if you want an out of the box solution. But there's an way. You can pretty much do it using a couple of UNIX and AT ([Hayes](https://en.wikipedia.org/wiki/wp%3EHayes_command_set "https://en.wikipedia.org/wiki/wp>Hayes_command_set")) commands.

## On locked/unlocked voice function

I don't remember how to check for it, but there's a custom command for querying voice stuff which works on most 3G dongles: `AT^CVOICE?`. Under normal circunstances, this command should give you audio format information. If it does not, either your 3G dongle doesn't support it at all or it's simply unlocked.

Unlocking it is a though proccess. And, the last time I checked, you had to pay some shaddy Indians to be able to do it using their software. I had to do it because I did some dumb stuff I won't go into detail here, but had something to do with firmware _quid-pro-quos_. So, please avoide messing with firmware unless you absuletly know what you are doing.

## How it works

Well, there were, in fact, a way to use the voice function under Linux. But it was cumbersome. Asterisk had a module called “chan\_dongle” which allowed those dongles to be used as trunk lines. If you just want to place a goddam call on your dongle, it's way to much work, I think. But it was the very existence of this module which proved to me it was possible to get the voice data without needing aditional crapware.

So, let me explain briefly how this voice stuff works in this kind of dongle: there's three serial ports (MODEM, DIAG and PCUI), and you talk to the modem via the MODEM port (generally is the first serial device, like /dev/ttyUSB0, but not always) or the PCUI port (which tends to be last one). The PCUI port isn't exactly useful because it outputs a lot of information which is only useful to the Partner Software. Then there are the middle one: DIAG. This pors seems to serve no purpose lack the hability to reply to AT commands. In the Huawei AT Command reference (cf. \[2\], p. 113 – PDF p. 111), though, there's a command (`AT^DDSETEX=2`) which lets you route the audio data through this DIAG port.

Typically, it shows up at `/dev/ttyUSB1`. But, as I said before, maybe you should test each port to find out which is which. To sumarize: DIAG port won't do anything, MODEM port replies to AT commands and PCUI does that and also prints some information from time to time, autoissuing some AT commands.

AT+CSQ
+CSQ: 11,99

OK
AT^SYSINFOEX
^SYSINFOEX:2,1,0,1,,3,WCDMA,41,WCDMA

OK

I won't go into details over this, however. I can think of some reasons for it to happen, but they're not really important for us, right now. Hypothesis: has something to do with keeping the network/signal status updated on whatever program uses it.

There's also a fourth port, mentioned in this document \[idem, ibid\] only once: PCVOICE. This is a hell of an unknown interface. From what I could tell, has something to do with HiLink devices, but doesn't apply to us. Even on Windows I saw the Partner Software send an `AT^DDSETEX=2` when dialing. So, the DIAG port is, as far we know, the most important piece to this puzzle.

**Note** _The audio PCM data goes through the DIAG port and you need to do is pipe it out through aplay as well as pipe it in via arecord, for the microphone to work_.

## In practice

Now, it's time to get practical. I won't absolutely dive into details here because the main reason I'm writing this is for myself, in the future. But, if you're not me, doesn't hurt to Google it up or read some of the references I left down below.

First thing, `screen /dev/ttyUSB0`, which is, mostly likely, the MODEM port (you might be in for some trial and error, here, as I already said enough times). Query it up: send in an simple `AT` commando. It should reply with `OK`. If it doesn't do this, this is the DIAG port, which is important but not yet.

Next, you need to find out if your dongle supports voice, so do as follows:

AT^CVOICE?                  <- The command you should send
^CVOICE: 0, 8000, 16, 20    <- The answer

OK <- The standard answer to any successful command

Write down the second and the third numbers. They'll be important very soond.

At this point, you are pretty much all set to place a call (given it's registered on the network, which you can check by UNIX cli: `mmcli -m 0` – not always 0, but you can check with `mmcli -l`). But, first, you need to make sure this audio hits your ears, so, according to \[3\], do this:

*   `sudo cat /dev/ttyUSB1 | aplay -f S16_LE`
    
*   `sudo arecord -f S16_LE /dev/ttyUSB1`
    

Both of those commands hangs the terminal, so you may want to open two terminals, use screen or whatever. Too lazy to explain. Also, running as root, you may run into a issue with the audio input/output. In this case, maybe it's sufficient to specify the device, like `-D “hw:1,0”` or whichever seems to be the right one.

Then, you come back to the MODEM port console. The important commands are:

*   `AT^DDSETEX=2`, which you need to issue everytime you call (because, by default, it routes the PCM data to the oblivion or the non-working mysterious PCVOICE port, _dunno_);
    
*   `ATD[phonenumber];` (the semicolon is very important, trust me… Otherwise you get `NO CARRIER` answers)
    
*   `AT+CHUP` to hang up on the call.
    

## References

*   \[1\] [Hayes Command Set on Wikipedia](https://en.wikipedia.org/wiki/Hayes_Command_Set "https://en.wikipedia.org/wiki/Hayes_Command_Set")
    
*   \[2\] [Huawei CDMA Datacard AT Command Interface](/_media/huaweicdma_at.pdf "huaweicdma_at.pdf (666.3 KB)") (Really important document about special commands for most 3G Huawei cards)
    
*   \[3\] [https://askubuntu.com/questions/464661/way-to-call-through-huawei-modem-in-14-04-e303](https://askubuntu.com/questions/464661/way-to-call-through-huawei-modem-in-14-04-e303 "https://askubuntu.com/questions/464661/way-to-call-through-huawei-modem-in-14-04-e303")
    
*   \[4\] [https://stackoverflow.com/questions/8367864/how-make-use-of-the-voice-api-to-make-calls-using-huawei-3g-modems](https://stackoverflow.com/questions/8367864/how-make-use-of-the-voice-api-to-make-calls-using-huawei-3g-modems "https://stackoverflow.com/questions/8367864/how-make-use-of-the-voice-api-to-make-calls-using-huawei-3g-modems")
