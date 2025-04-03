---
layout: default
title: TrampleTek Blue UI & Controls
nav_order: 8
---

# Explanation of the User Interface (UI) entities of the TrampleTek Blue

## User Interface Overview

<img src="images/HA_UI_overview.png" width="600">

### The UI has four visible entities **"Calibration"**, **"Dropdown Sensitivity"**, **"Sensitivity"**, and **"Mat Sensor"**.

Your UI entities may show up in a different order, and I will explain them from simplest to most complex. Note: I will use "pressure" and "weight" interchangeably in this section, they are technically different but for ease of examples I use them interchangeably.

### Mat Sensor monitor

<img src="images/HA_UI_binary.png" width="600">

This entity is as simple as it gets, it just shows when the mat has been triggered on or off. This is most likely the entity you will use to trigger your HA automations.

### Dropdown Sensitivity

<img src="images/HA_UI_dropdown.png" width="600">

(WARNING: ALL MATS HAVE SLIGHTLY DIFFERENT SENSITIVITY, take all weight values below as rough estimates as they could differ greatly from one mat to another.)

This dropdown lets you choose the mat’s sensitivity level. The five options are long to help explain them in the UI, the options are:

**1) Low weight object (<1 lb) on an uncovered mat, or a heavy weight object on a heavy weight covered mat (e.g. adult human with mat under mattress). Very sensitive, may cause false triggering**

- This option makes the mat very sensitive, so sensitive that it may trigger when it imagines something on it. This setting is not recommended unless you are trying to use it as a bed occupancy monitor.

**2) Low weight object (~1 lb) on an uncovered mat, or a heavy weight object on a medium weight covered mat (e.g. adult human with mat under rug)**

- This option is great for making sure your mat triggers for light packages or animals, it is the recommended default setting for high sensitivity with very few mistakes.

**3) Medium weight object (~1-20 lb) on an uncovered mat, or a heavy weight object on a light weight covered mat (e.g. adult human with mat under light rug)**

- This option is for triggering the mat with sizable objects, it may still trigger for small animal and packages, but if you put the mat under a cushion or rug then it will take a grown adult amount of weight to trigger the mat.

**4) Heavy weight object (>20 lb) on an uncovered mat, not likely to work well if mat is covered**

- This option is for triggering the mat only with heavy objects, this will likely never trigger for small or medium sided animals or packages. This is a great option if you want to use the mat to detect a car tire.

**5) Custom**

- This means you've selected a custom sensitivity from the "Sensitivity" slider.

### Sensitivity

<img src="images/HA_UI_sensitivity.png" width="600">

You can manually change the sensitivity of the mat with this slider. Increase this value to have the mat trigger on/off only on heavier weights, or decrease this value to have the mat trigger on/off on a lighter weight.

### Calibration

<img src="images/HA_UI_calibration.png" width="600">

If you're not sure what the Sensitivity should be for your use case use, use the Calibration button!

**<ins>How to use the Calibration button:</ins>**
- Load your mat with whatever you want the mat’s starting condition to be (e.g. put it under the couch cushion, put it under another mat etc.).
- Wait 30 seconds for the mat signal to fully settle
- Switch the Calibration button to "On"
- Put whatever the object you want to sense on the mat (e.g. sit on the cushion, stand on your top covering mat, etc.)
- The Sensitivity slider will automatically update to roughly where you should set the Sensitivity for your use case
- Switch the Calibration button to "Off"

Calibration is not perfect! You may want to move the Sensitivity slider around a little bit to fine tune when the mat triggers on/off.

## Diagnostic UI entities

<img src="images/HA_UI_overview_diag.png" width="400">

### There are five diagnostic entities **"Internal Temperature"**, **"Pressure Voltage"**, **"Reset Counter"**, **"Voltage measurement update rate (0 is off)"**, and **"WiFi Signal Strength"**.
From simplest to most complex:

### Internal Temperature
The internal temperature of the CPU, there to check how hot the device is getting!

### WiFi Signal Strength
The WiFi signal strength for your device. If it's always larger than -60dB you might want to consider moving it closer to your WiFi router, or getting a WiFi extender.

### Reset Counter
This counts how many times the mat has restarted, it's mostly for debugging reasons. It counts up to 5 and then restarts the counter to 0.

### Voltage measurement update rate (0 is off)
You can turn on the voltage output from the sensor by increasing this value above 0. This will enable you to view the "**Pressure Voltage**" entity. The fastest rate is 1 (updates every 1 second) and the slowest is 300 (updates every 300 seconds, i.e. 5 mins).

### Pressure voltage

With this UI entity you can watch the voltage of the mat change when something is placed on or taken off the mat. 

<img src="images/HA_UI_VoltagePlot.png" width="600">

This is an example of the voltage plot as I stand on and off the mat with one and then two feet. This UI entity is a fun way to explore the mat and you can even use voltage changes to trigger automations.

## Extra: Technical notes
- The Sensitivity value is the voltage change required to trigger "on" for the mat. The "off" trigger is a lower percentage of the Sensitivity value. This is because the mat can recover slowly from heavy or large objects and requiring less of a voltage change when weight comes off helps increase the responsiveness of the mat. You can get rid of this by removing the variable "scaleThreshold" in the YAML code. Look for this line **matUpThreshold = matDataAvg + id(step_event_threshold) * scaleThreshold; // Recovery can be slower, reduces the threshold requirement**

- The voltage change for the same weight can be different depending on how much weight is already on the mat (e.g. the first 10lbs on the mat might change the voltage by 0.5 V but another 10lbs may only change the mat voltage by an additional 0.1 V). The mats are tuned to be very sensitive to low weights, <20 lbs), but struggle to tell the different between 100 lbs and 1000 lbs. Below is a sweet MS Paint graphic to explain why higher weights sometimes need a *lower* sensitivity value:
  
<img src="images/SensitivityCurve.png" width="600">
  
- **<ins>Every mat's voltage range and sensitivity is different</ins>**. Textiles and soft stretchy materials do not always line up the exact same way for each mat build, so there is an expected, and sometimes sizable, variability between mats. If you have multiple mats, do not expect the same Sensitivity level to work for all your mats for the same use case.

Please join the [ASC Discord server](https://discord.gg/cB9P6NmYJg) if you have questions or comments about this page.

## Secret button for Travis

<esp-web-install-button manifest="https://raw.githubusercontent.com/ASCKing9/TrampleTek-Blue-code/refs/heads/main/TrampleTek_Debug/WeightExclusionBeta/TrampleTekBlue_ExWeight.json" install-supported="">
        <i slot="unsupported">
          The option is not available because your browser does not support Web
          Serial. Open this page in Google Chrome or Microsoft Edge instead<span class="not-supported-i hidden">
            (but not on your iOS device)</span>.
        </i>

<script
  type="module"
  src="https://unpkg.com/esp-web-tools@10/dist/web/install-button.js?module"
></script>
