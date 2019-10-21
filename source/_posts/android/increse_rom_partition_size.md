---
title: "[GUIDE] Increase your Nexus 4 s system partition for more space!"
date: 2019-10-18 10:37:05
categories:
- Flash ROM
tags:
- Android
- recovery
- Nexus4
- XDA
url: https://forum.xda-developers.com/nexus-4/general/guide-increase-nexus-4s-partition-space-t3800264
---

I got tired of installing amazing ROMs created by the talented folks here on XDA, but being held back on things like Google Apps because of the tiny /system partition we have on the Nexus 4. I looked around and found guides to increase the system space in the Nexus 5 and Nexus 7 2013, so I basically just adapted them to work on our beloved Nexus 4.

> As always, do this at your OWN risk. I am not responsible for bricking your Nexus 4. I will simply list the process which I used to increase my Nexus 4's system partition (by taking a big ol' chunk from the cache partition). Remember, any sort of modification to your device of this caliber WILL void any warranty you might still have.


#### REQUIREMENTS:
parted (Uploaded to [my Google Drive](https://drive.google.com/open?id=15uhtjeH2Z4DQywbRafrJs5cw7rmhnRG_). If it downloads as a .txt, rename it to remove the extension and make it a plain file)
adb and fastboot, and preferably knowledge on how they work


- Step 1: Install TWRP onto your Nexus 4 and reboot into it.
- Step 2: Open up command prompt / terminal and check to see if your Nexus 4 is connected properly with "adb devices".
- Step 3: Once you've confirmed that adb is fully working and your Nexus 4 is properly connected to your PC, download parted and use adb to push it to your Nexus 4 using the command:
  > adb push parted /
- Step 4: Now enter the following command:
  > adb shell

  and then the command:
  > chmod +x parted

  This will enter adb shell and make the "parted" binary you pushed to your device earlier executable.

- Step 5:
  Now run the command
  > ./parted /dev/block/mmcblk0 p

  You should see a long list with a bunch of numbers and names in your terminal. These are the partitions on your device. parted will give you the partition number, the "start" and "end" of the partition, the size, and the name.
  This is the partition layout on my device. It will probably be the same on your device, though the size of userdata may vary depending on whether you have the 8gb or 16gb Nexus 4.
  > ~ # ./parted /dev/block/mmcblk0 p
  >   Model: MMC 016G92 (sd/mmc)
  >   Disk /dev/block/mmcblk0: 15.8GB
  >   Sector size (logical/physical): 512B/512B
  >   Partition Table: gpt
  >
  >   Number  Start   End     Size    File system  Name      Flags
  >    1      524kB   67.6MB  67.1MB  fat16        modem
  >    2      67.6MB  68.2MB  524kB                sbl1
  >    3      68.2MB  68.7MB  524kB                sbl2
  >    4      68.7MB  70.8MB  2097kB               sbl3
  >    5      70.8MB  71.3MB  524kB                tz
  >    6      71.3MB  94.4MB  23.1MB               boot
  >    7      94.4MB  117MB   23.1MB               recovery
  >    8      117MB   118MB   799kB                m9kefs1
  >    9      118MB   119MB   799kB                m9kefs2
  >   10      119MB   120MB   799kB                m9kefs3
  >   11      120MB   121MB   524kB                rpm
  >   12      121MB   121MB   524kB                aboot
  >   13      121MB   122MB   524kB                sbl2b
  >   14      122MB   124MB   2097kB               sbl3b
  >   15      124MB   124MB   524kB                abootb
  >   16      124MB   125MB   524kB                rpmb
  >   17      125MB   125MB   524kB                tzb
  >   18      125MB   126MB   524kB                metadata
  >   19      126MB   143MB   16.8MB               misc
  >   20      143MB   159MB   16.8MB  ext4         persist
  >   21      159MB   1040MB  881MB   ext2         system
  >   22      1040MB  1627MB  587MB   ext4         cache
  >   23      1627MB  15.8GB  14.1GB  ext4         userdata
  >   24      15.8GB  15.8GB  524kB                DDR
  >   25      15.8GB  15.8GB  507kB                grow

- Step 6: Now run the following three commands:
> umount /data
> umount /sdcard
> umount /cache

- Step 7: So, on my Nexus 4, the system partition is number 21, and cache is 22. We're kinda lucky in the fact that system and cache are right next to each other, meaning we don't have to touch any other partition.
  You\'ll want to run these two next commands. These commands will essentially "remove" the two partitions.
  > ./parted /dev/block/mmcblk0 rm 21
  > ./parted /dev/block/mmcblk0 rm 22

- Step 8: Now it is time to recreate these two partitions, however, when recreating them, we will make system bigger and the cache smaller. From the partitions list we got in Step 5, we can see that system starts at 159 and ends at 1040, while cache starts at 1040 and ends at 1627. The following two commands will rebuild /system starting at 159, but ending at 1590, while rebuilding cache at 1590, and ending at 1627. We are essentially stealing a large chunk from cache, since we don\'t really need that anymore on newer ROMs.
  > ./parted /dev/block/mmcblk0 mkpart primary 159 1590
  > ./parted /dev/block/mmcblk0 mkpart primary 1590 1627

- Step 9: Now run this command:
  > ./parted /dev/block/mmcblk0 p

  This will bring up the partitions list, or table, again. This time, however, we\'ll see the new partitions where system and cache were, however, they have no names! The following two commands will name the two partitions again.

  > ./parted /dev/block/mmcblk0 name 21 system
  > ./parted /dev/block/mmcblk0 name 22 cache

- Step 10: Great! Now the partitions should be named again! Now, we still have to format the partitions as ext4 so that we can actually use them. The following two commands will do that for you.

  > mke2fs -b 4096 -T ext4 /dev/block/mmcblk0p21
  > mke2fs -b 4096 -T ext4 /dev/block/mmcblk0p22

- Step 11: At this point, feel free to run the command from Step 5 to take one more look at the partition table and make sure everything looks good. Now run the command

  > mount -a

  and then type in

  >exit

- Step 12: Now we are pretty much done. We\'ve extended the system partition from approx. 881mb to 1431mb, which is a nice large chunk of memory. In the future, we could always mess with the partitions more to add even more space by stealing from userdata, but until we reach that point, I think we are pretty well set for now!

Now...
You\'ll want to reboot TWRP, and flash a new ROM. You can now use a much bigger Google Apps package, without any worries.
Do note, however, that flashing a ROM will "resize" system to be smaller, but this isn't a huge deal. After flashing a ROM, while still in TWRP, you'll want to go to Wipe > Advanced Wipe > check "system" then head to "Repair or Change File System", > then tap on "Resize File System." If you encounter any errors while trying to resize, try remounting system or rebooting TWRP. Afterwards, you should be able to flash your Google Apps package. I'm not sure if you need to repeat these steps after flashing things other than ROMs, but repeating this process within TWRP should work just as well.

I hope I helped y'all out and feel free to post if this guide worked for you or if you have any other comments!

CREDITS:
@surfrock66 for his Nexus 5 guide [here](https://forum.xda-developers.com/google-nexus-5/general/guide-repartition-nexus5-to-increase-t3509880).
@rkhat for his Nexus 7 2013 guide [here](https://forum.xda-developers.com/nexus-7-2013/general/guide-repartition-nexus72013-to-t3599907).
