# JVC AC Chassis RGB Mod
### (AV-32D202, AV-32D302, AV-32D502)

<img src="https://i.imgur.com/uIfDkXu.jpg" width="600" />

RGB Mod for JVC AC CRT televisions. Also applies to similar model numberss within the GC chassis.

Written by Brendan Eddy (FlyingFlygon)

## Overview

This JVC D-Series chassis includes support for analog RGB through the micom's OSD video signals. You can tap in between the OSD's output and the Y/C Jungle's input to inject your external RGB signals through a common connector such as SCART or BNC. In this guide we will be utilizing SCART, made easier with help of Sunthar's mux board, more on that later. 

This mux mod will utilize the OSD circuit for RGB, Component Luma for sync, and direct connection with SCART pin 16 for blanking.

## Schematics

| Stock OSD RGB circuit | External RGB Mux Mod |
|---|---|
|<img src="https://i.imgur.com/wmAMSPs.png" width="400" />|<img src="https://i.imgur.com/7lplwfu.png" width="400" />|

## Components Needed

* 4 1n4148 diodes
* 3 360 Ohm resistors
* 3 75 Ohm resistors
* 3 1k Ohm resistors
* 1 4.7k Ohm resistor
* 1 SCART female port
* Plenty of different colored wire
* (Optional) Sunthar SCART mux board

## Modification Steps

1. Remove grounding SMD resistors R793, R794, R795

<img width="400" src="https://i.imgur.com/4XxsFDZ.png" />   <img width="400" alt="2" src="https://i.imgur.com/ke4V6wM.png" />

2. Replace OSD jumper wires with inline 1n4148 diodes. These wires are W296 (blanking), W543 (blue), W302 (red), W301 (green). Make sure the cathode end is towards the jungle as shown.

<img width="353" alt="3" src="https://i.imgur.com/dfioags.png" /> <img width="400" src="https://i.imgur.com/fVRJ1HB.jpg" />

<img width="300" alt="5" src="https://i.imgur.com/ui6nCFC.png" /> <img width="300" alt="6" src="https://i.imgur.com/1oRicFM.png" /> <img width="300" alt="7" src="https://i.imgur.com/sv9sNRs.png" />

3. At the end of these OSD lines they will connect through the unpopulated PIP connector CN003 and then enter 0 Ohm resistors before traveling to the jungle. These holes for the PIP header are convenient, as we can use them to bring the signals up to the top of the board. Standard header pins (for arduinos, etc) will fit but it's a tight squeeze. This is the route I chose. Optionally add header pins to the PIP pins 1-5. They are as follows:

* 1: ground
* 2: blanking
* 3: blue
* 4: green
* 5: red

Finally, solder some wires (or use quick connectors, but I avoid these due to interference/noise) to these on the top of the board, make sure they have enough length to reach the case where you will mount your external connectors (SCART, etc).

<img width="350" alt="8" src="https://i.imgur.com/Rc1amm8.png" /> <img width="300" alt="9" src="https://i.imgur.com/Cap4jsG.png" /> <img width="300" alt="10" src="https://i.imgur.com/6gHoBoM.png" />

4. Attach the rest of the wires necessary for your connector. If you're using SCART, you'll need wires for audio left and right. Regardless of SCART/BNC, you'll also need to attach a wire to the Component Luma pin for sync. Solder them at the pins like so. Make sure you use the component and audio jacks for Video 2. (I forgot to take a pic of my green wire - see the schematic for where it should go though).

<img width="350" alt="11" src="https://i.imgur.com/JBbWkd8.png" /> <img width="300" alt="13" src="https://i.imgur.com/XJmyU4q.png">
 <img width="350" alt="12" src="https://i.imgur.com/ZTO2E54.png" />

5. Assemble the SCART connector resistors and diodes. Using a [mux board from Sunthar](https://sector.sunthar.com/guides/crt-rgb-mod/rgb-mux.html) here helps a lot with the wiring.

* Factory inline RGB resistors: 2.2k Ohm
* Additional RGB inline resistors: 370 Ohm (made from what I had, you can also make 350 and 360 work)
* RGB termination resistors: 75 Ohm
* RGB and blanking lines all use diodes (as shown in step 2 above)
* Blanking inline resistor: 1k Ohm
* Blanking diode added from SCART pin 16 side
* Blanking ground resistor added since it was missing from factory (R796). Use 4.7k Ohm
* 1k Ohm resistors added to audio lines

<img src="https://i.imgur.com/4kYdx5b.jpg" width="400" /> <img src="https://i.imgur.com/PZ8DRCC.jpg" width="400" />

7. Cut a hole in the back case for the SCART connector. Depending on if you're using a mux board, directly wired to SCART, or even using BNC or RCA, you should have plenty of options of locations. I chose above the input panel.

<img src="https://i.imgur.com/UnMcSoB.jpg" width="400" /> <img src="https://i.imgur.com/gFtG1Gq.jpg" width="400" />

8. Insert a cut RCA jack into the Right audio channel in order to signal to the set to use stereo audio over SCART. If you omit this step, your audio will be mono. (Don't get confused at the fact my RCA is white. It's just what I had. Insert it into the red (Right audio) jack).


## Differences by Model

* AV-32D502 has PIP, so you may want to attach your wires to the pads of the 0 Ohm resistors instead of the througholes in the connector. Here's where that is on the schematic:
<img width="400" alt="99" src="https://i.imgur.com/rnZtVec.png" />


## Results

<img src="https://i.imgur.com/pP8kMzh.jpg" width="500" />
<img src="https://i.imgur.com/qOfqpDV.jpg" width="500" />
<img src="https://i.imgur.com/JSrRTOD.jpg" width="500" />
<img src="https://i.imgur.com/9JY7GnA.jpg" width="500" />
<img src="https://i.imgur.com/cY91wVK.jpg" width="500" />
<img src="https://i.imgur.com/Qc4S2be.jpg" width="500" />
<img src="https://i.imgur.com/BVe3BTw.jpg" width="500" />
<img src="https://i.imgur.com/5fDiyTQ.jpg" width="500" />

## Sources and Further Readings

* This chassis is similar to smaller JVCs but the mod is not identical. Take some inspiration from [Sunthar's guide here](https://sector.sunthar.com/guides/crt-rgb-mod/jvc-av-27230.html#schematics)

