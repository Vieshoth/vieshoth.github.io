---
layout: post
comments: true
categories: Linux
title: PARTITIONING MEMORY
---

## Introduction

Partitioning is a process of dividing the memory logically. All the non volatile memories can be partitioned.

In linux, there is a handy command called fdisk.
fdisk and sfdisk(does the same work as fdisk but in a different manner)

“fdisk -h” command gives you an idea about what it does and how it should be used.
```shell
 └─ $ ▶ fdisk -h

Usage:
 fdisk [options] <disk>      change partition table
 fdisk [options] -l [<disk>] list partition table(s)

Display or manipulate a disk partition table.

Options:
 -b, --sector-size <size>      physical and logical sector size
 -B, --protect-boot            don't erase bootbits when create a new label
 -c, --compatibility[=<mode>]  mode is 'dos' or 'nondos' (default)
 -L, --color[=<when>]          colorize output (auto, always or never)
                                 colors are enabled by default
 -l, --list                    display partitions end exit
 -o, --output <list>           output columns
 -t, --type <type>             recognize specified partition table type only
 -u, --units[=<unit>]          display units: 'cylinders' or 'sectors' (default)
 -s, --getsz                   display device size in 512-byte sectors [DEPRECATED]
     --bytes                   print SIZE in bytes rather than in human readable format

 -C, --cylinders <number>      specify the number of cylinders
 -H, --heads <number>          specify the number of heads
 -S, --sectors <number>        specify the number of sectors per track

 -h, --help     display this help and exit
 -V, --version  output version information and exit

For more details see fdisk(8).

```

## Knowing about sectors and bytes


Here for this example, let us take emmc as our device to partiton.
It has its device nod as “/dev/mmcblk0” in linux.

Provide this node as an input argument to fdisk command.
you will get an output similar to the output in the below shown image.

```shell
 └─ $ ▶ sudo fdisk /dev/mmcblk0
[sudo] password for i18342: 

Welcome to fdisk (util-linux 2.27.1).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.


Command (m for help): 
```

Inside the fdisk command prompt press m and enter. It will give the available options.
```
Command (m for help): m

Help:

  DOS (MBR)
   a   toggle a bootable flag
   b   edit nested BSD disklabel
   c   toggle the dos compatibility flag

  Generic
   d   delete a partition
   F   list free unpartitioned space
   l   list known partition types
   n   add a new partition
   p   print the partition table
   t   change a partition type
   v   verify the partition table
   i   print information about a partition

  Misc
   m   print this menu
   u   change display/entry units
   x   extra functionality (experts only)

  Script
   I   load disk layout from sfdisk script file
   O   dump disk layout to sfdisk script file

  Save & Exit
   w   write table to disk and exit
   q   quit without saving changes

  Create a new label
   g   create a new empty GPT partition table
   G   create a new empty SGI (IRIX) partition table
   o   create a new empty DOS partition table
   s   create a new empty Sun partition table


Command (m for help): 

```

To get the device details and the partition table type p and enter.
```shell
Command (m for help): p
Disk /dev/mmcblk0: 7.4 GiB, 7948206080 bytes, 15523840 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000


```

You will get an output similar to this.
This output shows the number of bytes and sectors this eMMC device has. Since this emmc device is not partitioned yet it doesn’t show any partitions.

It shows this emmc has 7818182656 bytes (that is 7.3 GB) and 15269888 number of sectors.
Sector is known as the smallest part of the memory.

From the same above image it shows the size of the sector as 512 bytes.
So if you divide the total bytes with 512 you will get number of sectors.

Partition is done in terms of sectors.


## Creating partition


We are going to create three partitions in this emmc.

First partition with 100MB and fat file system
Second partitin with 3GB and ext3 file system
Third partition with ramaining memory and fat file system

so lets start partitioning the eMMC

* Inside the fdisk command prompt press n and enter
* It will ask for partition type. Select the 'p' option for primary.
* And then select the partition number, since this is our first partition we go with the default one.
* The sector doesnot start with 0. Because it needs some space to store partition table and some meta data. Here in this eMMC it starts from 2048. So we too go with the defualt value.
* And then the last sector. That means where the partition should end. To this we need to do a small calculation. As we said earlier our first partition should have 100MB. To find the last sector divide the 100MB with 512 bytes and add 2018

Ex: (100*1024*1024/512) + 2048 = 206848
now give the last sector value as 206848 and press enter.
```shell
Command (m for help): n
Partition type
   p   primary (0 primary, 0 extended, 4 free)
   e   extended (container for logical partitions)
Select (default p): p
Partition number (1-4, default 1): 
First sector (2048-15523839, default 2048): 
Last sector, +sectors or +size{K,M,G,T,P} (2048-15523839, default 15523839): 206848

Created a new partition 1 of type 'Linux' and of size 100 MiB.
```
Now we have created our first partition. To check it press p.

![atl text](https://raw.githubusercontent.com/Vieshoth/vieshoth.github.io/master/images/part/p.png)


Now lets create the second partition
leave the first sector as default. that is 208896.
Can you notice the gap 2048 bytes between the last sector of the first partion and first sector of the second partition. That space is used to store meta data.

Now lets calculate the last sector.

last sector = (3*1024*1024*1024/512) + 208896
= 6500352

![atl text](https://raw.githubusercontent.com/Vieshoth/vieshoth.github.io/master/images/part/n2.png)

now go and check whether it is showing the first partition size as 3GB by pressing 'p'.

![atl text](https://raw.githubusercontent.com/Vieshoth/vieshoth.github.io/master/images/part/p2.png)

So we have created two partiotions. Did you notice the type of this partition? It shows the type is Linux. But we want that first partition as Fat32. In linux systems when you create a partition the default partition type is ext3 (which is shown as Linux).


## Chnaging the type of the partition

Now lets change the first partition type to FAT32. But how do we do it?. 
* Type m and search for the command to change the partition type. 
* Command ‘t’ is used to change the partition type. So type 't' and press enter. 
* Next it will ask for which partition to be selected for this operation. Give the partition numeber an input. 
In this case it is '1'. 
* Now to check the available partiton type press “L”. You will find out for FAT32 format, the hexcode is “c”.

![atl text](https://raw.githubusercontent.com/Vieshoth/vieshoth.github.io/master/images/part/hexcode.png)

Now check out the partition type by pressing “p”

![atl text](https://raw.githubusercontent.com/Vieshoth/vieshoth.github.io/master/images/part/p3.png)

Lets create the third and final partition and chenge the partition type to FAT32.

![atl text](https://raw.githubusercontent.com/Vieshoth/vieshoth.github.io/master/images/part/n3.png)

![atl text](https://raw.githubusercontent.com/Vieshoth/vieshoth.github.io/master/images/part/t.png)

now press “p” and check the created partitions.

![atl text](https://raw.githubusercontent.com/Vieshoth/vieshoth.github.io/master/images/part/p4.png)

Once the partitions are created format it with appropriate commands.


## Formating partition

To format FAT32 partition we have command called mkfs.vfat.

The syntax is: sudo mkfs.vfat <partition_device> -n <name>

For ext3

The syntax is: sudo mkfs.ext3 <partition_device> -L <name>

![atl text](https://raw.githubusercontent.com/Vieshoth/vieshoth.github.io/master/images/part/boot.png)

Ok now you know how to partition a eMMC or sdcard.

## SFDISK Command 

There is another way of doing this with just one command. That command is sfdisk. Open a partition.sh file using any editer and add the following lines.

```
echo “#############partitioning…#################”
node=/dev/mmcblk0

dd if=/dev/zero of=${node} bs=1024 count=1

sfdisk –force -uM ${node} << EOF
3,103,0c
104,2766,83
2767,,0c
EOF
```
save it, change the mode of the file and execute. 

This script will create partition, change the type of the partition and format it onbehalf of us.

Let us analyse this line by line.

```
dd if=/dev/zero of=${node} bs=1024 count=1
```
This line deletes the existing partition table if any.

```
sfdisk –force -uM ${node} << EOF
```
This line will start partitioning. 
```
3,103,0c
```
This line will create the first partition.
The first argument '3' represents the starting byte of  the partition interms of MB
The second argument '103' represents the size of the partition
And the third argument "0c" represents the partition type



Hope this article helps in understaing the concept of partitioning the memory in linux based OS.

Please type you feedback and comments in the comments section.

