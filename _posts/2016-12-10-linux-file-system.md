---
title: "Linux Filesystem"
categories: [computer-science, linux]
---

Linux filesystem dates back to late 1960s, the early days of Unix. Most of the folders are three to four letters long, starting with:

### /bin

Binary programs or executable files which are available to all users.

Includes GNU basic command line utilities essential to the system, such as ls, echo, grep etc. 

Also includes GUI applications

### /boot

Files essential to the booting of the system, such as:

- Vmlinuz - Linux Kernel
- System.map - Memory locations for variables or functions
- Initrd.img - Initial ramdisk, temporary root file system
- Grub
- EFI

### /dev

Files for peripheral and component devices of your system:

- /dev/js0 - First analogue joystick
- /dev/nvme0 - First NVMe drive
- /dev/sda - First SATA HDD / SSD
- /dev/loop0 - First fake mounting point
- /dev/null - Black Hole
- /dev/random or /dev/urandom - Random number generator
- /dev/zero - Zero

### /etc

Configuration files for all programs. However, user specific configs are stored in /home/user/.config

### /home

Users Documents, Pictures, Videos, etc.

User specific config settings are stored in /home/user/.config as well as other . (dot) folders.

### /lib

Shared library files and kernel modules.

Oftern ends with .so (Shared Object) extension.

- /lib/modules - Kernel modules
- /lib/x86_64 - Architecture specific
- /lib32 /lib64 - Architecture specific

### /media

Removable media, such as CD, DVD, USB Flash drive.

### /mnt

Fixed drives, such as SATA Hard drive or Solid State Drives.

### /opt

Additional applications which are not part of the default system.

This folder is an alternative to /bin, /usr/bin, /usr/local

### /proc

Pseudo file system which provides an interface to kernel view of processes (e.g. currently running applications). Referred to by PID (Process ID).

### /root

Root users home folder, usually empty if there is no root user on the system. This is not the same as /home/root .

### /sbin

Binary programs or executable files which are reserved for access by Root user. Similar to /bin

Includes basic command line utilities, such as: blkid, iptables, mount, useradd and visudo.

Also includes some GUI applications, although not as many as /bin

### /srv

Contains data which is served by the system, such as Website or FTP server. 

/var/www is also a location where website data is stored.

### /sys

Sysfs pseudo-filesystem which provides an interface to kernel view of hardware devices.

Lists more devices than /dev, such as CPU and Firmware.

### /tmp

Temporary files which are deleted on shutdown or reboot.

### /usr

Contains programs and libraries installed by the distro:

- /usr/bin - Applications which are available to all users
- /usr/sbin - Applications which are reserved for access by Root user
- /usr/games - Specific folder for games
- /usr/include - C Header files
- /usr/lib - Library files
- /usr/local - Folder for anything locally installed by the system administrator. (Not touched by the distro)
- /usr/share - Manual pages and other documents for applications


### /var

Variable data files which may regularly change, such as log files and printer spool

- /var/backups - Backups of key system files
- /var/cache - Cached data for applications
- /var/crash - Crash data dumps
- /var/lib - Dynamic libraries listed by owner application
- /var/lock - Locked files
- /var/log - Log data
- /var/spool - Spool files for cron, Mail and printing
- /var/tmp - temporary files which need to exist for longer than /tmp allows
