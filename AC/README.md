# JVC AC Chassis RGB Mod
### (AV-32D202, AV-32D302, AV-32D502)

<img src="" width="600" />

RGB Mod for JVC AC CRT televisions.

Written by Brendan Eddy (FlyingFlygon)

## Overview

This JVC D-Series chassis includes support for analog RGB through the micom's OSD video signals. You can tap in between the OSD's output and the Y/C Jungle's input to inject your external RGB signals through a common connector such as SCART or BNC. In this guide we will be utilizing SCART, made easier with help of Sunthar's mux board, more on that later. 

This mux mod will utilize the OSD circuit for RGB, Component Luma for sync, and direct connection with SCART pin 16 for blanking.

## Components Needed

TODO Brendan change this if 220 termination resistors ends up bad

* 4 1n4148 diodes
* 6 220 Ohm resistors (3 for RGB inline, 3 for RGB termination)
* 2 1k Ohm resistors
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


    1: ground
    2: blanking
    3: blue
    4: green
    5: red

Finally, solder some wires (or use quick connectors, but I avoid these due to interference/noise) to these on the top of the board, make sure they have enough length to reach the case where you will mount your external connectors (SCART, etc).

<img width="350" alt="8" src="https://github.com/brendanseattle/JVCRGBMod/assets/41927604/695acff2-d698-4db2-bbae-d66b9889bac2" /> <img width="300" alt="9" src="https://github.com/brendanseattle/JVCRGBMod/assets/41927604/5a2c7f51-0b0d-456d-ad86-1a556b1925ee" /> <img width="300" alt="10" src="https://github.com/brendanseattle/JVCRGBMod/assets/41927604/4063740f-9f21-4285-82ae-04c69475a55d" />

4. Attach the rest of the wires necessary for your connector. If you're using SCART, you'll need wires for audio left and right. Regardless of SCART/BNC, you'll also need to attach a wire to the Component Luma pin for sync. Solder them at the pins like so. Make sure you use the component and audio jacks for Video 2.

<img width="400" alt="11" src="https://github.com/brendanseattle/JVCRGBMod/assets/41927604/fef07d6e-a1c0-463a-a41f-343b3b62f703" /> TODO component pic <img width="400" alt="12" src="https://github.com/brendanseattle/JVCRGBMod/assets/41927604/99320e40-e9f5-4fa2-8d6f-7bd9202f6eb7" />


5. Assemble the SCART connector resistors and diodes. Using a mux board here helps a lot with the wiring. 

6. Cut a hole in the back case for the SCART connector.


## Differences by Model

* AV-32D502 has PIP, so you may want to attach your wires to the pads of the 0 Ohm resistors instead of the througholes in the connector. Here's where that is on the schematic:
<img width="400" alt="99" src="https://github.com/brendanseattle/JVCRGBMod/assets/41927604/b7f30d40-3059-4cbf-91fc-d0ea2f1904f8" />


## Notes, Tips, and Tricks


## Sources and Further Readings


