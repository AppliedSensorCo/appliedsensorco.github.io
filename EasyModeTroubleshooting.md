---
layout: default
title: Easy Mode Troubleshooting Tips
parent: Easy Mode Installation
nav_order: 2
---
# Easy Mode installation troubleshooting tips

## Sometimes things don't always go so smoothly, or you have a unique Home Assistant setup that adds a few unexpected hurdles! Hopefully one of these tips will help you.

## 1)  Home Assistant API encryption issues ([video link](https://youtu.be/4sYf2Vkg71Q?si=KegT5pdxMYknnxuy&t=280))

I haven't found a consistent reason that this issue comes up 🫤. The error often shows up soon after an install and may look something like this:

<img src="images/Expired_Auth_issue.png" width="600">

If you happen to know the encryption key you might be able to enter it after you click on the error, but typically the only solution is unfortunately to re-install the firmware to your device. That will recreate the encryption authentication.

## 2) ESPHome didn't automatically share your device IP with Home Assistant ([video link](https://youtu.be/4sYf2Vkg71Q?si=OFX0iIcHcgAUsIJX&t=314))

When you go to add your new ESPHome device into HA:

<img src="images/DeviceSetup_1_Config.png" width="600">

Instead of getting a pop up UI to easily add your device into Home Assistant you get this pop-up:

<img src="images/DeviceSetup_2_IPaddress.png" width="400">

The PORT should be 6053 (that's ESPHome's default port), but your IP address is unique to your device.

### At this point you will need to find your device's IP address, here are two methods: 

### Make sure your device is plugged into your computer, then connect it to the [ESP Web tools](https://web.esphome.io/) (you can go to the [Easy Mode Install](https://docs.asc.com/EasyModeInstall.html) instructions if you need help doing this).

### Option #1 for finding your device's IP:

If you see this dialog box (or maybe a similiar one with more options) click on "Visit Device":

<img src="images/Visit_device.png" width="400">

That will open up a new browser tab to your device and you can get the IP address from the web address line:

<img src="images/Visit_device_IP.png" width="600">

### Option #2 for finding your device's IP:

If "Visit Device" is not an option, click on "Logs & Console":

<img src="images/Logs_Console.png" width="400">

You will likely see a blank screen, and you may need to press the "Reset Device" button at the bottom of the Logs screen. That will prompt the device to restart and you'll see all the startup information. Scroll through it to this section to find your device's IP:

<img src="images/Logs_screen_reset_IP.png" width="600">

This [video link](https://youtu.be/4sYf2Vkg71Q?si=OFX0iIcHcgAUsIJX&t=314) explains how to do this with more detail.

### 3) Device seems to be constantly restarting ([video link](https://youtu.be/4sYf2Vkg71Q?si=KKhr6HFME9f2fJyz&t=391))

This is hard to tell if you are just powering the device with the USB cable to a plug, but if you connect your device into a computer you can hear the USB connection disconnect and reconnect sound over and over again. This means the firmware has been corrupted and you need to put the device into Boot Mode to get it out of the "boot-up -> fail -> restart -> boot-up" cycle. 

You will need to follow the [Boot Mode Instructions](https://docs.asc.com/bootmode.html) link and then you can re-install the firmware using the Easy Mode Install method.

### 4) There are always more bugs to fix and documentation to improve! If you have a problem not covered here email raymond@asc.com and I'll help you fix it, and maybe make a new section here about it 😁.

## Next Steps
**SKIP** the Manual Installation section and move directly to understanding the [UI elements of TrampleTek Blue](https://appliedsensorco.github.io/usingHAui.html) or the [UI elements of SlumberTek](https://docs.asc.com/SlumberTek.html)

Please join the [ASC Discord server](https://discord.gg/cB9P6NmYJg) if you have questions or comments about this page.
