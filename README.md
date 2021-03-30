# ChrBrunch
Brunch Framework(Chrome OS)

## Prepare images
### Latest release of Brunch Framework
https://github.com/sebanc/brunch/releases  

### Chrome OS recovery image
https://cros-updates-serving.appspot.com/

"rammus" is the recommended image for devices with 4th generation Intel CPU and newer.

"samus" is the recommended image for devices with 3rd generation Intel CPU and older.

"zork" is the image to use for AMD Ryzen 3XXX. (Higher Gen NOT SUPPORT YET)

"grunt" is the image to use for AMD Stoney Ridge.

## Install Chrome OS via USB
### Make USB flash drive to bootable
Extract Brunch Framework and Put recovery image(bin)

`cd /brunch[tab]`   

`lsblk` Check partition

Give an example of /dev/sdc as flash drive..

`sudo bash chromeos-install.sh -src [recovery image.bin] -dst /dev/sdc`   

### Install
go to boot menu and select flash drive

When it boots, `CTRL + ALT + T`   

Type `sudo chromeos-install -dst [Target, For example.. /dev/sdb]`   

## Make Multiboot
Script made by shrikant2002
https://raw.githubusercontent.com/shrikant2002/ChromeOS/master/multi_install.sh

Extract Brunch Framework and Put recovery image(bin) and Multi_install.sh

`cd /brunch[tab]`   

Script will only recognize the recovery named as `rammus_recovery.bin`     
So rename ur Recovery image `rammus_recovery.bin`     

`sudo sh multi_install.sh`   

## Just need img file only
Extract Brunch Framework and Put recovery image(bin)

`cd /brunch[tab]`   

`sudo bash chromeos-install.sh -src [recovery image.bin] -dst [name.img ex. chromeos.img]`   
