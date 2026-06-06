---
layout: page
title: Assembly
permalink: /assembly/
---
Disassembly of the Maclock is the hardest part of the entire project. Below is a step-by-step guide to disassembling the Maclock and preparing it for the installation of the Raspberry Pi and LCD display. I can only add that the process is quite tedious and that you are guaranteed to break at least one of the plastic clips. Make sure you break the clips at the bottom, because it is invisible and does not affect the aesthetics of the final product. Use a plastic prying tool to avoid damaging the case. Take your time and be patient.

<div style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden;">
    <iframe
        src="https://www.youtube.com/embed/WEVMEvV_sOM"
        style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;"
        frameborder="0"
        allowfullscreen>
    </iframe>
</div>


Once you have disassembled the Maclock, you will need to prepare the case for the installation of the Raspberry Pi and LCD display. The original instructable, linked below for your reference, reuses the original charging port by rewiring the charging socket board. I found this to be tedious. The wiring is fragile, and once soldered, the two parts of the maclock case cannot be separated without breaking the wires. Raspberry Pi Zero 2 W has a micro USB port for power, and there is no reason to not make use of it and try to use the probe pads on the Raspberry Pi for power instead. I left the original charging port in place, unconnected and cut two holes in the case back for two USB ports, one for power and one for the USB hub. I chose to use Micro USB to USB-C panel mount adapters for the ports, because they are sturdy and robust unlike the increasingly rare and fragile Micro USB ports.

Additionally, I cut a large hole in the back of the case for the CF card slot, so that I could easily reprogram the Raspberry Pi without having to open the case.

*Power switch*:
![Angled MicroUSB to USB-C panel mount](/media/usb_extension.png)
![Bypass](/media/power_board.png)    
I  cut one of the Micro USB to USB-C cables in half and inserted a DIY bypass with a switch, using a micro-JST pigtail and a piece of stripboard to allow to turn the power on and off without having to unplug the cable. It allowed me to use the mock floppy drive as a power switch, which is a nice touch, if I do say so myself.

For your build, you can follow the instructable below, with the appropriate adjustments. 
*Nota Bene!:* 
![](/media/dont_do_this.png)
The instructable calls for trimming the borders with a pair of side cutters. I found this to be entirely unnecessary, and I did not do it. The 3D printed LCD display frame fits perfectly in the original opening without any modifications, and the borders are not visible when the case is closed.

[Instructable](https://www.instructables.com/Wireless-Mini-Mac-From-a-Maclock/)

The video below takes this project one siginificant step further than I did by adding a custom PCB for the Raspberry Pi and reusing the the original brigtness control knob and two pushbuttons. It also adds an internal speaker for even greater authenticity. It is an amazing project, and if you feel adventurous, you can try to follow his instructions to add these features to your build as well.

<div style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden;">
    <iframe
        src="https://www.youtube.com/embed/zAbAf5-H5Yo"
        style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;"
        frameborder="0"
        allowfullscreen>
    </iframe>
</div>