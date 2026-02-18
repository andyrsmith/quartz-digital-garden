---
title: Linux Directories
date: 02/02/2026
tags:
  - linux
links:
id: "202602021517"
---
# Linux Directories

The following is a breakdown of what each directory is in the Linux system.

## /

The Linux root directory is the base of all other directories.  
It is just listed as a / with no name to it. All other directories start with the root directory

## /bin 

The bin directory contains executable files that are available to all users. These executable files are basic shell commands like cp, mv, etc.

## /dev

The dev directory contains files relating to devices that are virtual files. These files act as an interface for hardware and kernel resources.

- /dev/null : Send files or strings here to be destroyed
- /dev/zero : Contains an infinate sequence of zeros
- /dev/random : Contains an ifinate sequence of random numbers

## /etc

This directory is where system configuration files are located.

Examples of files

- hostname
- passwd
- crontab

## /usr

This folders stands for User System Resource. This contains user executable files, libraries source of system programs, and documentation among other non-essentials files.

- /usr/bin : contains user executable files.
- /usr/sbin : non essentials administrator binaries.
- /usr/share : Documentation, icons, and fonts.

## /home

This is the user personal directory. Each user that has a login to a computer will have a folder contained in here.

/home/asmith

This will contain user specific config files and any personal files they create here. Other users will not have access to their folder unless they are given permission

## /lib

This contains code essential libraries and kernel modules that are need to boot the system and run commands in the /bin directory.
## /sbin

This directory has executable files that can only be used by the root user.

## /tmp

This is the temporary directory. Applications use this to store files that are not needed for the long term. Users can also use the directory for any temp file that they have.

Files here are usually automatically deleted by the system. This can happen when the system restarts.

## /var

This directory is used to stores information during the systems operation. This can be logging, tracking, and spool files and directory.

## /boot

Contains the Kernel, boot image, and other essential files needed to start the OS. Bootloaders like LILO and GRUB are store here. This directory sometimes resides on it's own partition.

## /proc

This directory contains information about the running processes and hardware on a Linux system. This includes virtual files that reside in RAM and not on the hard drive.

## /opt

This contains 3rd party software packages that are not apart of the core Linux experience. This might contain software like a web browser, chat client, etc.

## /media

This is the directory where removable media is accessed. Linux automatically creates a folder here when a drive like USB, SD, or CD/DVD becomes present.

## /mnt

This is a directory is where you manually mount different devices to. If you need to use the mount command to attach a media you attach the drive here.
## /srv

This directory contains services like the http and ftp server.



