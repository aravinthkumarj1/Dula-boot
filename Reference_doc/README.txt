********************SD CARD partition Details********************
RAW: 200MB
1-partition(vfat): 100MB
2-partition(ext4): min 1Gib



*************************Flash steps*****************************

u-boot flash:
-------------

sudo dd if=u-boot.imx of=/dev/mmcblk0 bs=512 seek=2

Wince NK.nb0 flash:
-------------------

sudo dd if=NK.nb0 of=/dev/mmcblk0 bs=512 seek=1026

Copy Wince eboot:
------------------

cp EBOOT.nb0 /media/(vfat partition)

Copy Linux 3.14.28 kernel:
--------------------------

cp imx6dl-sabresd.dtb /media/(vfat partition)

cp uImage /media/(vfat partition)


*************From linux uboot, change to windows steps***********

Read the eboot:
---------------

fatload mmc 1:1 0x10041000 EBOOT.nb0

Load the eboot:
---------------
go 0x10041c00
