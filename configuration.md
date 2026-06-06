---
layout: page
title: Configuration
permalink: /configuration/
---
Create a folder called `basilisk` in your home directory. This will be the main folder for all of your Basilisk II files, including the configuration, ROMs, and disk images.


Create a folder called shared under `basilisk`. This will be the shared folder that Basilisk II can access. You can put files here that you want to transfer between your host and the emulated Mac.


Create the image for your main drive. This will be the drive that you install the Mac OS on. You can use the `dd` command to create a blank image file. For example, to create a 2GB image:
```dd if=/dev/zero of=~/basilisk/main_drive.img bs=1M count=2048
   hformat ~/basilisk/main_drive.img -fs HFS+ -label "Macintosh HD"
```

Create the image for your transfer drive. This will be the drive that you use to transfer files between your host and the emulated Mac. You can use the `dd` command to create a blank image file. For example, to create a 512MB image:
```dd if=/dev/zero of=~/basilisk/transfer_drive.img bs=1M count=512
   hformat ~/basilisk/transfer_drive.img -fs HFS+ -label "Transfer"
```

Copy the configuration file .basilisk_ii_prefs to your home directory. This file contains the configuration settings for Basilisk II. You can edit this file to change the settings for your emulated Mac.

Copy the ROM file to your basilisk folder. This file is required for Basilisk II to run. You can obtain the ROM file from your own Mac or from the internet. Make sure to place it in the `basilisk` folder and update the configuration file to point to the correct location of the ROM file.

Copy the minimal boot image to your basilisk folder. This image is used to boot the emulated Mac and install the Mac OS. You can obtain this image from the internet. Make sure to place it in the `basilisk` folder and update the configuration file to point to the correct location of the boot image.

Copy the Mac OS 7.5.3 installation image to your basilisk folder. This image is used to install the Mac OS on the main drive. You can obtain this image from the internet. Make sure to place it in the `basilisk` folder and update the configuration file to point to the correct location of the installation image.

Launch Basilisk II.

Double click the CD icon and follow the prompts to install the Mac OS on the main drive. This will take a few minutes.

Download and install stuffit 5.5 expander on the emulated Mac. This will allow you to extract files from .sit archives, which are commonly used for Mac software distribution.