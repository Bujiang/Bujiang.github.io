---
layout: post
title: "Mount disk from Shell(Terminal) in Mac"
date: 2014-08-11 15:31:00 +0800
comments: true
categories: [OS X,BASH]
---

Before we mount disk or drive, we need to know all the connected first. There is a program called diskutil that can manipulate the structure of local disks.

Type diskutil list in shell, the program will list all the 
connected disks.

``` bash
diskutil list
```

The output will look like

``` bash
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *250.1 GB   disk0
   1:                        EFI EFI                     209.7 MB   disk0s1
   2:                  Apple_HFS Mac OS                  249.2 GB   disk0s2
   3:                 Apple_Boot Recovery HD             650.0 MB   disk0s3
/dev/disk2
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:        CD_partition_scheme                        *124.0 MB   disk2
   1:       CD_ROM_Mode_2_Form_1 A20110738               108.0 MB   disk2s0
```

Suppose will need mount the CD inside optical drive, we can type diskutil mountDisk /dev/disk2

``` bash
diskutil mountDisk /dev/disk2
```

After successful mount the disk, the output will look something like

``` bash
Volume(s) mounted successfully
```

For mounting disk the argument use in diskutil is mountDisk but normal extenal hard drive just use mount. 

Unmounting disk or drive use unmountDisk or unmount for argument

``` bash
diskutil mount /dev/disk3
diskutil unmount /dev/disk3
disktuil mountDisk /dev/disk2
disktuil unmountDisk /dev/disk2
```