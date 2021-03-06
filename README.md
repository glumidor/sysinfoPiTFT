# sysinfoPiTFT
startup script for Raspberry with small display (PiTFT) attached to it

 - you have a RaspberryPi
 - and you have an [Adafruit TFT Screen](http://www.adafruit.com/categories/97) (or similar) attached to your Raspberry

This script "sysinfoPiTFT" starts with booting, providing information about ram and disk usage,
tries to connect wpa_supplicant with any configured network and
prints out the hostname and the ip addresses to be able to ssh to.
There's an auto-refresh (first minute 30 sec, afterwards 120 sec)

The new version of [Adafruit's PiTFT display](http://www.adafruit.com/products/2423) comes with four buttons already attached, 
so this script prints a menu and checks the buttons every 0.5 sec.
There's a "shift button" to get more than just 4 menu entries, with this shift button there are 6 possibilities

To get more characters on your screen, reconfigure your console 

	dpkg-reconfigure console-setup

enter, enter, enter until you are asked for *Terminus* and some other fonts. Choose Terminus 6x12.
This gives you 40x26 (portrait) or 53x20 (landscape) characters and the Terminus font is way better readable.
The script is aware of portrait and landscape mode (*/boot/config.txt*) and prints a slightly different layout



# Installation

if not done yet, install figlet and bc

	apt-get install figlet bc

copy the script into the directory /etc/init.d

	cp sysinfoPiTFT/sysinfoPiTFT /etc/init.d/

and add it to the runlevel handling (for debian style runlevels)

	upgrade-rc.d sysinfoPiTFT defaults
	
	reboot
	
The script should start while booting the system, even before the login is shown.
When the script crashes, the boot sequence for this runlevel is finished and you'll be asked to login.


# Updating

when updating the script, you just need to replace the */etc/init.d/sysinfoPiTFT* file. it gets reloaded automatically
