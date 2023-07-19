# JVC AC Chassis RGB Mod
### (AV-32D202, AV-32D302, AV-32D502)

<img src="https://github.com/brendanseattle/JVCRGBMod/assets/41927604/72cfe860-6307-4bd8-b662-af6edc2c8e9c" width="600" />

RGB Mod for JVC AC CRT televisions.

Written by Brendan Eddy (FlyingFlygon)

## Overview

This JVC D-Series chassis includes support for analog RGB through the micom's OSD video signals. You can tap in between the OSD's output and the Y/C Jungle's input to inject your external RGB signals through a common connector such as SCART or BNC. In this guide we will be utilizing SCART, made easier with help of Sunthar's mux board, more on that later. 

This mux mod will utilize the OSD circuit for RGB, Component Luma for sync, and direct connection with SCART pin 16 for blanking.

## Schematics

| Stock OSD RGB circuit | External RGB Mux Mod |
|---|---|
|<img src="https://github.com/brendanseattle/JVCRGBMod/assets/41927604/94ff3e63-f72c-4adc-a393-56d6fd33ff46" width="400" />|<img src="https://github.com/brendanseattle/JVCRGBMod/assets/41927604/29454bf4-6b1e-4817-95b9-a23e973b506c" width="400" />|

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

<img width="400" src="https://github.com/brendanseattle/JVCRGBMod/assets/41927604/c53697e7-2c98-429f-bee5-56f444f5e11b" />   <img width="400" alt="2" src="https://github.com/brendanseattle/JVCRGBMod/assets/41927604/b3892256-acaa-494b-b935-5f21945d3c36" />

2. Replace OSD jumper wires with inline 1n4148 diodes. These wires are W296 (blanking), W543 (blue), W302 (red), W301 (green). Make sure the cathode end is towards the jungle as shown.

<img width="353" alt="3" src="https://github.com/brendanseattle/JVCRGBMod/assets/41927604/03ad6ea8-c54b-454e-9917-98b3a26a8af4" /> <img width="400" src="https://github.com/brendanseattle/JVCRGBMod/assets/41927604/878c4f45-4e2d-4fc2-a348-c9437d421a69" />

<img width="300" alt="5" src="https://github.com/brendanseattle/JVCRGBMod/assets/41927604/9c46a130-a463-43bc-963c-51304389ecad" /> <img width="300" alt="6" src="https://github.com/brendanseattle/JVCRGBMod/assets/41927604/8c1f2b57-1af5-401d-b535-285763d3192b" /> <img width="300" alt="7" src="https://github.com/brendanseattle/JVCRGBMod/assets/41927604/45d0b16e-8c21-477a-ae3b-9071be5d1c74" />

3. At the end of these OSD lines they will connect through the unpopulated PIP connector CN003 and then enter 0 Ohm resistors before traveling to the jungle. These holes for the PIP header are convenient, as we can use them to bring the signals up to the top of the board. Standard header pins (for arduinos, etc) will fit but it's a tight squeeze. This is the route I chose. Optionally add header pins to the PIP pins 1-5. They are as follows:

* 1: ground
* 2: blanking
* 3: blue
* 4: green
* 5: red

Finally, solder some wires (or use quick connectors, but I avoid these due to interference/noise) to these on the top of the board, make sure they have enough length to reach the case where you will mount your external connectors (SCART, etc).

<img width="350" alt="8" src="https://github.com/brendanseattle/JVCRGBMod/assets/41927604/695acff2-d698-4db2-bbae-d66b9889bac2" /> <img width="300" alt="9" src="https://github.com/brendanseattle/JVCRGBMod/assets/41927604/5a2c7f51-0b0d-456d-ad86-1a556b1925ee" /> <img width="300" alt="10" src="https://github.com/brendanseattle/JVCRGBMod/assets/41927604/4063740f-9f21-4285-82ae-04c69475a55d" />

4. Attach the rest of the wires necessary for your connector. If you're using SCART, you'll need wires for audio left and right. Regardless of SCART/BNC, you'll also need to attach a wire to the Component Luma pin for sync. Solder them at the pins like so. Make sure you use the component and audio jacks for Video 2. (I forgot to take a pic of my green wire - see the schematic for where it should go though).

<img width="350" alt="11" src="https://github.com/brendanseattle/JVCRGBMod/assets/41927604/fef07d6e-a1c0-463a-a41f-343b3b62f703" /> <img width="300" alt="13" src="https://github.com/brendanseattle/JVCRGBMod/assets/41927604/cc7b3376-677b-47e8-a423-48d853d3a5b3">
 <img width="350" alt="12" src="https://github.com/brendanseattle/JVCRGBMod/assets/41927604/99320e40-e9f5-4fa2-8d6f-7bd9202f6eb7" />


5. Assemble the SCART connector resistors and diodes. Using a [mux board from Sunthar](https://sector.sunthar.com/guides/crt-rgb-mod/rgb-mux.html) here helps a lot with the wiring.

* Factory inline RGB resistors: 2.2k Ohm
* Additional RGB inline resistors: 370 Ohm (made from what I had, you can also make 350 and 360 work)
* RGB termination resistors: 75 Ohm
* RGB and blanking lines all use diodes (as shown in step 2 above)
* Blanking inline resistor: 1k Ohm
* Blanking diode added from SCART pin 16 side
* Blanking ground resistor added since it was missing from factory (R796). Use 4.7k Ohm
* 1k Ohm resistors added to audio lines

<img src="https://github.com/brendanseattle/JVCRGBMod/assets/41927604/f2f54747-a8c5-40d4-b05b-48e12af78068" width="400" /> <img src="https://github.com/brendanseattle/JVCRGBMod/assets/41927604/2d6a11a5-006c-43a1-bc67-cc12bbd2b655" width="400" />

7. Cut a hole in the back case for the SCART connector. Depending on if you're using a mux board, directly wired to SCART, or even using BNC or RCA, you should have plenty of options of locations. I chose above the input panel.

<img src="https://github.com/brendanseattle/JVCRGBMod/assets/41927604/0d5bea42-a16f-4e8e-abfe-c632469b1163" width="400" /> <img src="https://github.com/brendanseattle/JVCRGBMod/assets/41927604/9f326a65-2601-477e-9fc3-969d947c2ba0" width="400" />

8. Insert a cut RCA jack into the Right audio channel in order to signal to the set to use stereo audio over SCART. If you omit this step, your audio will be mono. (Don't get confused at the fact my RCA is white. It's just what I had. Insert it into the red (Right audio) jack).


## Differences by Model

* AV-32D502 has PIP, so you may want to attach your wires to the pads of the 0 Ohm resistors instead of the througholes in the connector. Here's where that is on the schematic:
<img width="400" alt="99" src="https://github.com/brendanseattle/JVCRGBMod/assets/41927604/b7f30d40-3059-4cbf-91fc-d0ea2f1904f8" />


## Results

<img src="https://github.com/brendanseattle/JVCRGBMod/assets/41927604/68da2b40-d38f-4f34-a4d1-2a22ad926e7a" width="500" />
<img src="https://github.com/brendanseattle/JVCRGBMod/assets/41927604/a0e31f03-ada8-43f3-83df-a25c303293ab" width="500" />
<img src="https://github.com/brendanseattle/JVCRGBMod/assets/41927604/94284b2b-279e-436b-bcda-7e8664552e1b" width="500" />
<img src="https://github.com/brendanseattle/JVCRGBMod/assets/41927604/13fd2b5d-5b99-43e8-a02c-02a406baab72" width="500" />
<img src="https://github.com/brendanseattle/JVCRGBMod/assets/41927604/7c792738-70bf-498c-8e72-48d69f5e8387" width="500" />
<img src="https://github.com/brendanseattle/JVCRGBMod/assets/41927604/99b17d94-7cd7-4541-a6e0-d7e95665a9e9" width="500" />
<img src="https://github.com/brendanseattle/JVCRGBMod/assets/41927604/af30e230-72df-487a-a7da-cb47fb362c3d" width="500" />
<img src="https://github.com/brendanseattle/JVCRGBMod/assets/41927604/17da730a-b61a-4c83-bfac-67059d5e5955" width="500" />

## Sources and Further Readings

* This chassis is similar to smaller JVCs but the mod is not identical. Take some inspiration from [Sunthar's guide here](https://sector.sunthar.com/guides/crt-rgb-mod/jvc-av-27230.html#schematics)

