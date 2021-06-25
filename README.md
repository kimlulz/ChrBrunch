# ChrBrunch
Brunch Framework(Chrome OS)

## Prepare images
### Latest release of Brunch Framework
https://github.com/sebanc/brunch/releases  

### Chrome OS recovery image
https://cros-updates-serving.appspot.com/

"volteer" is the recommended image for devices with 11th generation Intel CPU. (need kernel 5.10)

"rammus" is the recommended image for devices with 4th generation Intel CPU and newer.

"samus" is the recommended image for devices with 3rd generation Intel CPU and older.

"zork" is the image to use for AMD Ryzen(4*** Model need kernel 5.10)

"grunt" is the image to use for AMD Stoney Ridge.

## Install Chrome OS via USB
### Make USB flash drive to bootable
Extract Brunch Framework and Put recovery image(bin)

`cd /brunch[tab]`   

`lsblk` Check partition

Give an example of /dev/sdc as flash drive..

`sudo bash chromeos-install.sh -src [recovery image.bin] -dst /dev/sdc`   

#### Install
go to boot menu and select flash drive

When it boots, `CTRL + ALT + T`   

Type `sudo chromeos-install -dst [Target, For example.. /dev/sdb]`   

## Just need img file only
Extract Brunch Framework and Put recovery image(bin)

`cd /brunch[tab]`   

`sudo bash chromeos-install.sh -src [recovery image.bin] -dst [name.img ex. chromeos.img]`   

### Make partition bootable via img and grub entry

make partition   
mount /dev/sdXY /mnt    
`sudo bash chromeos-install.sh -src [recovery image.bin] -dst /mnt/chromeos.img`   
Add grub entry via grub customizer


