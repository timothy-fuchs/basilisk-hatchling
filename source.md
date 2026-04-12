# Basilisk Hatchling
[media/basilisk__hatchling.png]

## Parts
* Raspberry Pi Zero W 2
* Waveshare 2.8" LCD monitor
* 
Lorem ipsum

## Installation process
* Correct at the time of writing *
* OS - raspbian Trixie Lite (headless)
** install with the default settings.
** Configure WiFi.
** Enable ssh.

** Configure the LCD
*Note: Waveshare Wiki is here: https://www.waveshare.com/wiki/2.8inch_DPI_LCD?spm=a2g0n.appdesc.0.0.130eA0ssA0ssp1&file=2.8inch_DPI_LCD*
*** Open the config.txt file in the root directory of the TF card, add the following code at the end of the config.txt and save:
```
dtoverlay=vc4-kms-v3d
dtoverlay=waveshare-28dpi-3b-4b   
dtoverlay=waveshare-28dpi-3b
dtoverlay=waveshare-28dpi-4b
dtoverlay=waveshare-touch-28dpi
dtoverlay=vc4-kms-dpi-2inch8
```
Download the DTBO file https://files.waveshare.com/wiki/2.8inc-DPI-LCD/28DPI-DTBO.zip , unzip and copy into /boot/overlays


** Ssh into the hatchling.

*** Enable VNC.
*** To correct screen orientation, add the following to the beginning of `/boot/firmware/cmdline.txt`, separate by space.
`video=DPI-1:480x640M@60,rotate=270`

*** Update the system
```
sudo apt update
sudo apt full-upgrade -y
sudo reboot
```

*** Install the prerequisites
```
sudo apt install -y \
    build-essential \
    git \
    autoconf \
    automake \
    libtool \
    pkg-config \
    libsdl2-dev \
    libasound2-dev \
    libslirp-dev \
    libgtk-3-dev \
    libgl1-mesa-dev \
    libgles2-mesa-dev
```



*** Download, configure, and build SDL2 (Headless / KMSDRM Only)
*Note: check the download page, download the latest release of SDL2 available. Do not download SDL3*
```
cd ~
wget https://libsdl.org/release/SDL2-2.32.10.tar.gz
tar xf SDL2-2.32.10.tar.gz
cd SDL2-2.32.10
```

** Configure SDL2 without X11, Wayland, PulseAudio, or OpenGL, and with KMSDRM
```
./configure \
    --disable-video-x11 \
    --disable-video-wayland \
    --disable-video-opengl \
    --disable-video-vulkan \
    --disable-pulseaudio \
    --disable-esd \
    --enable-video-kmsdrm \
    --enable-video-rpi \
    --enable-video-dummy
```
*** Build and install
```
make -j4
sudo make install
sudo ldconfig
```
This gives you a pure KMSDRM SDL2, ideal for headless Basilisk II.

** Clone and build Basilisk II
*Note: the credit for porting Basilisk II to SDL2 goes to kanjitalk755, but his implementation does not play nice with waveshare LCD panels. My fork does.*
```
cd ~
git clone https://github.com/timothy-fuchs/macemu.git
cd macemu/BasiliskII/src/Unix
```

*** Configure and build 
`./autogen.sh`

*** Configure Basilisk II for:

**** SDL2 video/audio
**** No X11
**** No GTK
**** No JIT (safer on ARM)
**** No VOSF
 
 ```
./configure     --enable-sdl-video     --enable-sdl-audio     --disable-vosf     --disable-jit     --without-x     --without-gtk     --disable-nls     --disable-esd     --disable-mon
```

Install the hfs utilities
`sudo apt install hfsutils`

Create the main drive image
dd ...
Create the transfer drive image

Create the basilisk configuration.
Mount the boot floppy disk
Boot - at this stage you should get 