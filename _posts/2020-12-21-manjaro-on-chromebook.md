---
layout: post
title: Installing Manjaro on Braswell Chromebooks
---

If you had issues with GalliumOS on your Braswell Chromebook like me (such as the low frame/refresh rate, or the system not locking the screen when the lid is closed), or just want to try something new, then this guide is for you! You'll be shown how to install Manjaro on your Chromebook and fix keyboard issues.

## 1. Installation

**Edit: I found that the minimal version of Manjaro KDE has less bugs for some reason. It's much more resource intensive though.**

Assuming you already have MrChromebox's firmware installed, [download the minimal version of Manjaro XFCE](https://manjaro.org/downloads/official/xfce/) and write the file to a USB drive (in my case, I had to use `sudo dd if=manjaro.iso of=/dev/sdb bs=4M status=progress && sync`).

Next, boot your Chromebook from that USB drive and install the system as usual. After the installation is complete, reboot your machine and unplug the USB (AKA "installation medium") if the system asks you to.

## 2. Fix the keyboard issues

Surprisingly, your Chromebook's audio (the internal mic doesn't work on any distro) should work without any extra configuation, unlike other distros (such as Ubuntu). I think this is caused because Manjaro, being based on Arch Linux, has the latest stable kernel thus having the nessecary drivers.

Anyway, back to the keyboard issues - your keyboard should work fine except for the media keys (volume up/down/mute, brightness, back/forward, etc). This can be fixed by adding a new keyboard layout that properly maps the media keys. Run the following commands in the terminal to add that layout:

```bash
mkdir -p /tmp/mediakeys
cd /tmp/mediakeys
wget https://github.com/optio50/ChromeBook-Keyboard-xkb/raw/master/xkb.zip
unzip xkb.zip
sudo rm -rf /usr/share/X11/xkb
sudo mv xkb /usr/share/X11/
```

Next, click on the Manjaro logo on the down-left corner, search for "keyboard" and press enter. Go to the "Layout" tab and change the keyboard model to `Chromebook (most models) | Search overlay | F keys mapped to media keys`.

## That's it

Congratulations, I guess! You've just installed Manjaro on your Chromebook.
