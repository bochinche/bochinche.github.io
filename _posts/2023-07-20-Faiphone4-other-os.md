---
layout: post
title:  "FairPhone 4: installing other Android flavours on this phone"
date:   2023-07-20 08:45:47 +0100
categories: management technology
---

## Tutorial: Installing CalyxOS, eOS, and the Original FairPhone OS on Fairphone 4

Before you proceed with the installation process, please ensure that you have backed up all your important data as unlocking the bootloader and installing custom operating systems may erase your data. Also, keep in mind that this tutorial assumes you are using macOS. Let's get started!

### Prerequisites:

1. Fairphone 4 with the latest software updates installed.
2. A computer running macOS.
3. USB cable to connect the Fairphone to the computer.
4. Enable Developer Options on your Fairphone: Go to Settings > About phone > Tap on "Build number" multiple times until you see a message confirming that Developer Options have been enabled.
5. Enable OEM Unlocking: Go to Settings > System > Developer options > Enable "OEM unlocking" and "USB debugging."

### Step 1: Unlock the Bootloader

1. Visit [Fairphone's Bootloader Unlocking Code page](https://www.fairphone.com/en/bootloader-unlocking-code-for-fairphone-3/) to obtain the bootloader unlock code. You'll need to provide the IMEI 1 and serial number of your Fairphone.

2. Once you have received the unlock code, power off your Fairphone.

3. Boot your Fairphone into fastboot mode by pressing and holding the Volume Down and Power buttons simultaneously.

4. Connect your Fairphone to the computer using a USB cable.

5. Open Terminal on your macOS computer.

6. Change to the directory where you downloaded the Android platform-tools (e.g., `cd /Users/YourUsername/Downloads/platform-tools/`).

7. In Terminal, enter the following command to unlock the bootloader using the unlock code you received:

   ```bash
   ./fastboot flashing unlock
   ```

   Follow the on-screen instructions on your Fairphone to confirm the bootloader unlocking process.

8. For additional security, you can also run the following command to lock the critical partitions after unlocking:

   ```bash
   ./fastboot flashing lock_critical
   ```

### Step 2: Installing CalyxOS

1. Download CalyxOS for Fairphone 4 from their official website: [CalyxOS Fairphone 4 Downloads](https://release.calyxinstitute.org/FP4-factory-23411000.zip).

2. Extract the downloaded ZIP file to a location on your computer.

3. Reboot your Fairphone into fastboot mode again:

   ```bash
   adb reboot bootloader
   ```

4. Set the environment variable to include the path to the platform-tools:

   ```bash
   export PATH=/Users/YourUsername/Downloads/platform-tools/darwin/:$PATH
   ```

5. Flash CalyxOS onto your Fairphone:

   ```bash
   fastboot flashall -w
   ```

   This command will erase all data on your phone, so make sure you've backed up anything important.

6. Once the process is complete, your Fairphone will reboot with CalyxOS installed.

### Step 3: Installing eOS

1. Download eOS for Fairphone 4 from their official website.

2. Connect your Fairphone to the computer in fastboot mode:

   ```bash
   adb reboot bootloader
   ```

3. Set the environment variable again if needed:

   ```bash
   export PATH=/Users/YourUsername/Downloads/platform-tools/darwin/:$PATH
   ```

4. Flash eOS onto your Fairphone:

   ```bash
   fastboot flashall -w
   ```

5. Your Fairphone will reboot with eOS installed.

### Step 4: Reverting to the Original FairPhone OS

If you wish to revert to the original FairPhone OS:

1. Download the Fairphone 4 original factory image from Fairphone's website or obtain it from their support page.

2. Connect your Fairphone to the computer in fastboot mode:

   ```bash
   adb reboot bootloader
   ```

3. Set the environment variable again if needed:

   ```bash
   export PATH=/Users/YourUsername/Downloads/platform-tools/darwin/:$PATH
   ```

4. Flash the original FairPhone OS factory image onto your Fairphone:

   ```bash
   fastboot flashall -w
   ```

5. Your Fairphone will reboot with the original FairPhone OS installed.

That's it! You've successfully installed CalyxOS, eOS, and the original FairPhone OS on your Fairphone 4. Remember that flashing custom ROMs and unlocking the bootloader can void your warranty, so proceed with caution and make sure you understand the risks involved. Enjoy exploring these different operating systems on your Fairphonad!

### Links 

- <https://antoineggg.medium.com/installing-e-os-on-fairphone-4-6d7dfb208d94>
- <https://community.e.foundation/t/install-e-on-fp4-on-mac/38591/7>
- <https://developer.android.com/tools/releases/platform-tools>
- <https://support.fairphone.com/hc/en-us/articles/10492476238865>
- <https://doc.e.foundation/pages/install_easy_installer/win_fp4>
- <https://doc.e.foundation/devices/FP4/install>
- <https://doc.e.foundation/build-status>