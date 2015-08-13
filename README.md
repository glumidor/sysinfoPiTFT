# sysinfoPiTFT
startup script for Raspberry and small display (PiTFT) attached to it

 - you have a RaspberryPi
 - and you have an adafruit TFT Screen on top of your Raspberry

This script "sysinfoPiTFT" starts with booting, providing information about ram, disk, ip addresses
to be able to get the (dhcp) ip address to ssh to.

To get more characters on your screen, *dpkg-reconfigure console-setup* and choose Terminus 6x12
this gives you 40x26 (portrait) or 53*20 (landscape) characters
the script is aware of portrait and landscape and prints a slightly different layout



# Installation
copy the script into the directory /etc/init.d

make it executable with chmod +x /etc/init.d/sysinfoPiTFT

add to the runlevel handling with upgrade-rc.d sysinfoPiTFT defaults
