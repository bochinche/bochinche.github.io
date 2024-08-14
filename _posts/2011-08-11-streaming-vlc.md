---
layout: post
title:  "on VLC stream to Airport Express"
date:   2011-08-11 08:00:00 +0100
categories: IT iOS VLC
---

Hello Readers,

Last week I picked up an Apple Airport Express as a bargain on eBay.
I am quite impressed with the quality of the wireless signal and the fact that you can stream audio to wirelessly connected speakers.

iTunes recognizes the wireless speakers right away, if you are connected to the same network, of course. However, I wanted to stream not only music, but also audio from videos, YouTube, etc.

There is a nice program from rouge amoeba called AirFoil that lets you do that. At the time of writing, there were still some issues with OSX Lion that needed to be fixed. The software costs $25, which I was not willing to pay. If you are willing to pay, do so, it is a very nice piece of work.

Going back to my open source roots, and since VLC is my favorite media player, I decided to give it a try since the ROAP protocol was newly implemented and according to some sources it worked well with AirTunes.

I could not find a nice how-to on the web, so I decided to write down what I did to get it to work:

1. Go to VLC Preferences -> All -> Stream Output and write the following in the "Default stream output chain" field
#duplicate{dst="transcode:raop",dst=display}

![screenshot1](/assets/images/streaming_vlc1.png)

2. Go to VLC Preferences -> All -> Stream Output -> South Stream -> Transcode Options and enter the following options

Destination audio codec: alac
Audio channels: 2
Audio sample rate: 44100

3. Go to the VLC Preferences -> All -> Stream Output -> Sout Stream -> RAOP Options and enter the following options

Host: the IP address of your Airport device
Password: the password you use in iTunes to stream music (Note: do not set if you do not have one)

4. Finally, go to VLC Preferences -> All -> Audio and set the following option

Audio desynchronization compensation: -3000

Hope this helps!