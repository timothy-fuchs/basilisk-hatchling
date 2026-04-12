---
layout: page
title: Prerequisites
permalink: /prerequisites/
---
# OS
Since we are going to be using the SDL2 library, the X11 framework is a hinderance, so we will not install it at all.
Use Raspberry Pi imager to flash Raspberry Pi Lite OS 32 bits
![Raspberry Pi OS Lite - 32 bits.](/media/os-imager.png)

NB!: Further instructions are assuming that you chose the default account name.

Flash the image on the CF card.

# Waveshare LCD drivers
*Note: Waveshare Wiki is here: https://www.waveshare.com/wiki/2.8inch_DPI_LCD?spm=a2g0n.appdesc.0.0.130eA0ssA0ssp1&file=2.8inch_DPI_LCD*
Please read it before proceeding, since the process of deploying their driver may change.

Open the config.txt file in the root directory of the TF card, add the following code at the end of the config.txt and save:
```
dtoverlay=vc4-kms-v3d
dtoverlay=waveshare-28dpi-3b-4b   
dtoverlay=waveshare-28dpi-3b
dtoverlay=waveshare-28dpi-4b
dtoverlay=waveshare-touch-28dpi
dtoverlay=vc4-kms-dpi-2inch8
```
Download the DTBO file https://files.waveshare.com/wiki/2.8inc-DPI-LCD/28DPI-DTBO.zip , unzip and copy into /boot/overlays

*At this stage, you should be ready to insert the CF card with the OS image into your Raspberry Pi card reader and boot into the OS.*

```
sudo raspi-config
```
Enable ssh access.


# TODO: rotate the screen via cmdline.txt


# Build prerequisites
Since we will be building the SDL2 library and Basilisk II emulator from the source, we need to install the build tools.