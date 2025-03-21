---
layout: default
title: (Optional) Taking Control of the TrampleTek mat in ESPHome
parent: Easy Mode Installation
nav_order: 1
---
# (Optional) Taking Control of the TrampleTek mat in ESPHome

## These instructions are optional and only if you want to view device Logs and edit the YAML code directly after doing the [Easy Mode Installation](https://appliedsensorco.github.io/EasyModeInstall.html).

## If you "Take Control" of your TrampleTek Blue, you will still get Home Assistant notifications when there is an update. IF YOU UPDATE YOUR FIRMWARE THROUGH HOME ASSISTANT OTA (Over-the-air) after you have "Taken Control" of the device then IT WILL ERASE YOUR INTERNALLY SAVED WI-FI CREDENTIALS. You will need to use Bluetooth, or the device's fallback hotspot, or connect via the [ESPHome web](https://web.esphome.io/), or reload the firmware completely using the [Easy Mode instructions](https://appliedsensorco.github.io/EasyModeInstall.html) to get the device reconnected to your Wi-Fi. Alternatively you can look through the [TrampleTek Blue YAML code](https://github.com/ASCKing9/TrampleTek-Blue-code/blob/main/TrampleTek_WebUSB_ESPHome.yaml) to make the updates yourself instead of using Home Assistant's OTA update.

## These are the step-by-step instructions to "Take Control" of your TrampleTek Blue device in ESPHome.

- Open a Home Assistant tab, typically [http://homeassistant.local:8123/](http://homeassistant.local:8123/), and open ESPHome in the Settings -> Add-ons section.

<img src="images/select_addons.png" width="600">

- Select ESPHome.

<img src="images/select_ESPHome.png" width="600">

- Open the Web UI.

<img src="images/select_open_web_UI.png" width="600">

- Your mat will be discovered, but hidden. Click on the "Show" in the top right corner.

<img src="images/USBWeb_15_show_devices.png" width="600"> 

- Click on the "Take Control" once you see the device.

<img src="images/USBWeb_16_take_control.png" width="600"> 

- Give your mat a useful name. I find short but descriptive is best, I picked "Raymond's Mat". Click "Take Control".

<img src="images/USBWeb_17_name_device.png" width="400"> 

- Now install with your new name! Click "Install".

<img src="images/USBWeb_18_install.png" width="400"> 

- This part is going to take awhile, like 3-4+ minutes. It's going to build the code and then install it over Wi-Fi. Make sure your mat is in a good place for signal from your router. The underlined bar shows the progress of installing over the Wi-Fi. Sometimes this step fails, go to the bottom of this page for help.

<img src="images/USBWeb_19_install_logs.png" width="600">
  
- Eventually you should see this, and you can close the window. Your device's UI element names should all be updated with your new name, and you can view the YAML code and device logs in the ESPHome UI.

<img src="images/USBWeb_20_close_logs.png" width="600"> 

### I have seen an Wi-Fi install error that says something like "Error resolving IP address: Error resolving address with mDNS:" when trying to "Take Control". Sometimes you just need to press "Retry" in the bottom right of LOGS screen (the screenshot above will have a "Retry" button if the upload fails). If that doesn't work, make sure your ESPHome SECRETS has your Wi-Fi information.

- Get to the ESPHome UI view and click on “Secrets” in the top right corner. 

<img src="images/ESPHome_secrets.png" width="600"> 

-	If this file is empty, follow the structure of the information in the image and put in your SSID and password inside the double quotations just like the made up Wi-Fi details below. Click Save.

<img src="images/ESPHome_secrets_yaml.png" width="600">

- Then go to ESPHome UI and click on "EDIT" for the device and try to install again.

<img src="images/ESPHome_mat_edit.png" width="600"> 

<img src="images/ESPHome_mat_yaml_save_upload.png" width="600"> 

## Next Steps
**SKIP** the Manual Installation section and move directly to [understanding the UI elements of the TrampleTek Blue (Home Assistant version)](https://appliedsensorco.github.io/usingHAui.html).

Please join the [ASC Discord server](https://discord.gg/cB9P6NmYJg) if you have questions or comments about this page.
