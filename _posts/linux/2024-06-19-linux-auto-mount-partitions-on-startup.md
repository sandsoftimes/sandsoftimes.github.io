---
layout: post
title: Linux Configuration for Auto-Mounting Disk
date: 2024-06-19 20:52:55.000000000 +05:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Linux
- Utilities
tags: []
meta:
  _wpas_done_all: '1'
author:
  login: SandsOfTime
  email: janeebee1092@gmail.com
  display_name: SandsOfTime
  first_name: Muhammad
  last_name: Sharjeel Akhtar
permalink: "/2024/06/19/linux-configuration-on-auto-mounting-disk"
---
By default if you've multiple Disk-Drives or partitions, either in NTFS or FAT partition system, linux donot automatically mount them. You've to mount the partition everytime manually which is honestly way too headache for a lazy person like me. Why not solve this issue and do some configurations so that on boot the linux automatically mount all the disk-drives. 

For this purpose you've to add your drives in the `fstab` file,

```
sudo nano /etc/fstab
```

Here you'll see already added the linux drives by default. In my case i've 4 NTFS partitions from my Windows-Drive and i want to mount them automatically on startup. I'll add the `UUID` of the drives in this text file. 

Simply open your disk management application on your linux (I'm using linux mint and also i've tried the same method on ubuntu, works totally fine for me).

![1](/assets/images/clt/linux-auto-mount-partitions-on-startup/1.png)

I've 4 Hard-Drives. The last one is this linux itself so ignore it and lets focus on the first 3. Click on the first Drive and you'll see something like this,

![2](/assets/images/clt/linux-auto-mount-partitions-on-startup/2.png)

The text-file opened in your terminal, it has the following syntax to add partitions.

```
UUID=581EDE4F1EDE2632 /media/saleemshady/hdd2 ntfs defaults 0 2
```

First of all copy the `UUID` of this partition from the disk software. In the text-editor write a new line following the same syntax. Replace the UUID with the UUID of your partition. Next check the partition type (whether it is fat,ntfs e.t.c) and write accordingly after the path and the remaining syntax will be same. 

P.S here you can get the partition-type and UUID from the disk-software,

![3](/assets/images/clt/linux-auto-mount-partitions-on-startup/3.png)

Similarly do the same for other partitions as well. In my case it looks like this,

![4](/assets/images/clt/linux-auto-mount-partitions-on-startup/4.png)

Now save the file using the shortcut key of `CTRL+O` and exit from the editor using `CTRL+X`. 

The configuration is completed. Now whenever you linux will boot. It will automatically mount all the partitions by default. 

