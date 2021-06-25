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

## Just make image files.
Extract Brunch Framework and Put recovery image(bin)

`cd /brunch[tab]`   

`sudo bash chromeos-install.sh -src [recovery image.bin] -dst [name.img ex. chromeos.img]`   

### Make partition bootable via img and grub entry
make partition   
mount /dev/sdXY /mnt    
`sudo bash chromeos-install.sh -src [recovery image.bin] -dst /mnt/chromeos.img`   
When it finished,
```
 ChromeOS disk image created.

To boot directly from this image file, add the lines between stars to either:
- A brunch usb flashdrive grub config file (then boot from usb and choose boot from disk image in the menu),
- Or your hard disk grub install if you have one (refer to you distro's online resources).
********************************************************************************
menuentry "ChromeOS" --class "brunch" {
	rmmod tpm
	img_part=/dev/sdxY
	img_path=/mnt/chrome.img
	search --no-floppy --set=root --file $img_path
	loopback loop $img_path
	linux (loop,7)/kernel boot=local noresume noswap loglevel=7 options= \
		cros_secure cros_debug loop.max_part=16 img_part=$img_part img_path=$img_path \
		console= vt.global_cursor_default=0 brunch_bootsplash=default quiet
	initrd (loop,7)/lib/firmware/amd-ucode.img (loop,7)/lib/firmware/intel-ucode.img (loop,7)/initramfs.img
}

menuentry "ChromeOS (debug mode)" --class "brunch-debug" {
	rmmod tpm
	img_part=/dev/sdxY
	img_path=/mnt/chrome.img
	search --no-floppy --set=root --file $img_path
	loopback loop $img_path
	linux (loop,7)/kernel boot=local noresume noswap loglevel=7 options= \
		cros_secure cros_debug loop.max_part=16 img_part=$img_part img_path=$img_path
	initrd (loop,7)/lib/firmware/amd-ucode.img (loop,7)/lib/firmware/intel-ucode.img (loop,7)/initramfs.img
}
********************************************************************************


If you have Ubuntu or Linux Mint installed, you can create the grub config automatically by running the below command:
********************************************************************************
echo -e '#!/bin/sh\nexec tail -n +3 $0\n\n\n\n'"$(sed '1,4d;$d' $(realpath "chrome.img").grub.txt)" | sudo tee /etc/grub.d/99_brunch && sudo chmod 0755 /etc/grub.d/99_brunch && sudo update-grub
********************************************************************************
If you use this command, remember that your grub configuration will be in the file /etc/grub.d/99_brunch, you will need to modify this file if you want to enable Brunch options.

```

type below command `echo -e '#!/bin/sh\nexec tail -n +3 $0\n\n\n\n'"$(sed '1,4d;$d' $(realpath "chrome.img").grub.txt)" | sudo tee /etc/grub.d/99_brunch && sudo chmod 0755 /etc/grub.d/99_brunch && sudo update-grub` to add grub entry.    
or use grub customizer for add manually via /mnt/chrome.img.grub.txt


if you need to change kernel version(Ryzen 4*** or Intel Gen11), Change grub options like below
![chr_kernel_before](https://user-images.githubusercontent.com/42508318/123405260-9a204d00-d5e4-11eb-9613-f21405fd0bf2.png)
![chr_kernel_after](https://user-images.githubusercontent.com/42508318/123405275-9db3d400-d5e4-11eb-81b2-7be01621360d.png)
