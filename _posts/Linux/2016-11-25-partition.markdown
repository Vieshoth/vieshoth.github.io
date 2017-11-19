---
layout: post
comments: true
categories: Linux
title: PARTITIONING MEMORY
---

### Introduction

Partitioning is a process of dividing the memory logically. All the non volatile memories can be partitioned.

In linux, there is a handy command called fdisk.
fdisk and sfdisk(does the same work as fdisk but in a different manner)

“fdisk -h” command gives you an idea about what it does and how it should be used.
![atl text](https://raw.githubusercontent.com/Vieshoth/vieshoth.github.io/master/images/part/fdisk_command.png)


### Knowing about sectors and bytes


Here for this example, let us take emmc as our device to partiton.
It has its device nod as “/dev/mmcblk0” in linux.

Give this node as an input argument to fdisk command.
you will get an output similar to the output in the below shown image.
![atl text](https://raw.githubusercontent.com/Vieshoth/vieshoth.github.io/master/images/part/fdiskmmcblk.png)

Inside the fdisk command prompt press m and enter. It will give the available options.
![atl text](https://raw.githubusercontent.com/Vieshoth/vieshoth.github.io/master/images/part/fdiskm.png)

To get the device details and the partition table type p and enter.
![atl text](https://raw.githubusercontent.com/Vieshoth/vieshoth.github.io/master/images/part/partitiontype.png)

You will get an output similar to this.
This output shows the number of bytes and sectors this eMMC device has. Since this emmc device is not partitioned yet it doesn’t show any partitions.

It shows this emmc has 7818182656 bytes (that is 7.3 GB) and 15269888 number of sectors.
Sector is known as the smallest part of the memory.

From the same above image it shows the size of the sector as 512 bytes.
So if you divide the total bytes with 512 you will get number of sectors.

Partition is done in terms of sectors.


### Creating partition


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

Screenshot from 2016-08-05 11:15:33
![atl text](https://raw.githubusercontent.com/Vieshoth/vieshoth.github.io/master/images/part/n.png)

Now we have created our first partition. To check it press p.Screenshot from 2016-08-05 11:16:04
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


### Formating partition

Now lets change the first partition type to FAT32. But how do we do it?. Type m and search the for the command to change the partition type. Command ‘t’ is used to change the partition type. So type and press enter. It will ask for which partition we should change the type. press 1 for that. And then press “L” and check what are the available partition type.

For FAT32 the hexcode is “c”.
![atl text](https://raw.githubusercontent.com/Vieshoth/vieshoth.github.io/master/images/part/hexcode.png)

Now check out the partition type by pressing “p”

![atl text](https://raw.githubusercontent.com/Vieshoth/vieshoth.github.io/master/images/part/p3.png)

Lets create the third and final partition and chenge the partition type to FAT32.

![atl text](https://raw.githubusercontent.com/Vieshoth/vieshoth.github.io/master/images/part/n3.png)

![atl text](https://raw.githubusercontent.com/Vieshoth/vieshoth.github.io/master/images/part/t.png)

now press “p” and check the created partitions.

![atl text](https://raw.githubusercontent.com/Vieshoth/vieshoth.github.io/master/images/part/p4.png)

Once the partitions are created format it with appropriate commands.

To format FAT32 partition we have command called mkfs.vfat.

The syntax is: sudo mkfs.vfat <partition_device> -n <name>

For ext3

The syntax is: sudo mkfs.ext3 <partition_device> -L <name>

![atl text](https://raw.githubusercontent.com/Vieshoth/vieshoth.github.io/master/images/part/boot.png)

Ok now you know how to partition a eMMC or sdcard.

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
save it change the mode of the file and execute. It will does all the work for us. Ok now lets explore how does it work?

The second line creates a variable and assigns the device which must be partitioned.

The third line deletes the already availabe partition  table .

The fifth line is where we actually going to partition. In the sixth line we create the first partition.

3 – starting byte of  the partition interms of MB

103 – size of the partition

0c – partition type
