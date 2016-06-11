---
title: Adding a new disk to Oracle Linux 7 VirtualBox VM using LVM
layout: post
tags: Linux UEK
---

Add a new disk to the VM in the VirtualBox Manager GUI :

Click storage for the VM and add a new disk to the controller, either create a new disk or add and existing disk.

Start the VM and check the new disk is visible using fdisk -l and then create a new partition on it. In this example I'm adding a new disk sdb to an existing volume group ol.

fdisk /dev/sdb

n 1 return t 1 8e w

pvcreate /dev/sdb1

Add the new physical volume to an existing volume group

vgextend ol /dev/sdb1

Create a new logical volume in the ol volume group

lvcreate -L 100G -n newvol2 ol

Create a file system on the new volume :

mkfs.xfs /dev/ol/newvol2

Add a entry to /etc/fstab for the new volume and mount point

 vi /etc/fstab

add

/dev/mapper/ol-newvol /newvol xfs defaults 0 0

create the directory /newvol for the mount point and mount the volume :

 mkdir /newvol
 mount /newvol
