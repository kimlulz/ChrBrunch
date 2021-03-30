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

## Make USB flash drive to bootable
Extract Brunch Framework and Put recovery image(bin)

`cd /brunch[tab]`   

`lsblk` Check partition

Give an example of /dev/sdc as flash drive..

`sudo bash chromeos-install.sh -src [recovery image.bin] -dst /dev/sdc`   

## Make img files
Extract Brunch Framework and Put recovery image(bin)

`cd /brunch[tab]`   

`sudo bash chromeos-install.sh -src [recovery image.bin] -dst chromeos.img`   
