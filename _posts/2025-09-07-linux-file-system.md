---
title: "LWM #2 - Linux File System"
tags: [Learn With Me, Linux, Linux Basics, Linux OS, Operating System, Fundamentals]
date: 2025-09-07
excerpt: Linux’s filesystem hierarchy from /, where everything begins. Learn what lives in /bin and /sbin (essential binaries), /boot (kernel and bootloader), /dev (device interfaces), /etc (system-wide configs), /home (user data), /lib (shared libraries), /media and /mnt (mounted storage), /opt (third-party apps), /root (root’s home), /tmp (ephemeral files), /usr (user-space programs, usr-merge), and /var (changing data like logs). Understand permissions, mounting behavior, and why modern distros symlink /bin, /sbin, and /lib to /usr.
---
#### NOTE: The contents of this post have not been copied from anywhere. I have researched and written each line in my own words including the diagram, so there may be minor inaccuracies or points I may have overlooked. I appreciate your understanding.

# Linux File System

In linux we know everything is a file, and there is a structure and hierarchy to these files, based on their usage and security.  
On the very top is **/** the root file-system and all the other sub-directories are inside this root file-system.  
These other sub-directories inside **/** are : **/bin, /sbin, /boot, /dev, /etc, /home, /lib, /media, /mnt, /opt, /root, /tmp, /usr, /var**  
  
  
<div style="display: flex; justify-content: center; margin-bottom: 100px; margin-top: 70px;">
  <img src="/assets/images/linux_file_system/linuxfilesystemdiagram.svg" alt="file-system" style="width: 100%; height: 100%;">
</div>
  
  
<div style="justify-content: start;">
  <img src="/assets/images/linux_file_system/bin.svg" alt="bin" style="width: 5%; height: 5%;">
</div>  
> bin is short for binary, as it stores binary files.  
What are binary files ? These are compiled programs.  
  
> If you have ever used C or C++, you need to first compile your program and then run it. That compiled program is also binary now, and if you execute it then it'll do it's specified job.  
  
> Similarly these bin files are executable binary files that are used by the system or used by us like ls, cp, mv, rm, cat etc..  
Even the apps you install using apt or dnf they drop their binaries in /usr/bin  
  
> **Modern systems with usr-merge uses /usr/bin, and /bin is just a pointer to /usr/bin**  
  
  
<div style="justify-content: start;">
  <img src="/assets/images/linux_file_system/sbin.svg" alt="bin" style="width: 5%; height: 5%;">
</div>  

> this is also a directory for binaries but it's for admin or root-user binaries  
  
  
<div style="justify-content: start;">
  <img src="/assets/images/linux_file_system/boot.svg" alt="bin" style="width: 5%; height: 5%;">
</div>  
> this is very important directory, it has all the bootloader and kernel files that system needs before it sets up the main file-system **/**  
so when you turn on your machine it loads the bootloader file in memory and then run kernel files(vmlinuz) and runs *initial ram file system*(initrd.img), then the Kernel mounts our main filesystem to **/** that has all the other subdirectories.  
  
  
<div style="justify-content: start;">
  <img src="/assets/images/linux_file_system/dev.svg" alt="bin" style="width: 5%; height: 5%;">
</div>  
> dev is short for device, it holds device files ( *here device means the hardware of the systems* ).  
  
> In linux we know everything is a file, so when an application wants to talk to the hardware they read or write to these device files directly, without needing device specific function calls.  
Its like **standard file based interface** for programs to interact with hardware and kernel services.  
  
> In contrast to this, a Windows OS uses drivers  
every hardware on windows has a driver and they implement device-specific APIs.  
  
  
<div style="justify-content: start;">
  <img src="/assets/images/linux_file_system/etc.svg" alt="bin" style="width: 5%; height: 5%;">
</div>  

> this directory holds system wide config/configuration files, system wide means global config files, so when you apply these, they are gonna affect all the users on the system.  
Some config files in /etc can be overridden by the user-specific-config files in their home directory.  
  
  
<div style="justify-content: start;">
  <img src="/assets/images/linux_file_system/home.svg" alt="bin" style="width: 5%; height: 5%;">
</div>  
> each user on the system gets their own seperate subdirectory in the /home directory.  
for example user1 gets /home/user1 that holds user1's personal files and directories similarly, user2 has /home/user2  
  
> So can user1 do cd /home/user2 and look at all the user2's files ?  
No! generally the permission doesn't allow a user to do that but if an admin gives read, write or execute permission it's possible.  
before: drwx- - - - - -  
after : drwxr-xr-x  
  
  
<div style="justify-content: start;">
  <img src="/assets/images/linux_file_system/lib.svg" alt="bin" style="width: 5%; height: 5%;">
</div>  
> this directory holds standard libraries.  
  
> *for example in C language you have to include stdlib on top of the program to use it's functions.*  
  
> similarly in this directory it has all the libraries that the system needs for its functionality and for running programs in /bin or /sbin  
  
  
<div style="justify-content: start;">
  <img src="/assets/images/linux_file_system/media.svg" alt="bin" style="width: 5%; height: 5%;">
</div>  
> when you plugin a removable media device like USB, CD, SSD. the system automatically mounts it here at /media. and you can access it at /media/user1/usb1  
  
> so can user1 do cd /media/user2/usb2 ?  
No! since it's automatically mounted so the initial permissions doesn't allow you to do that, but if you are given the permission you can.  
  
  
<div style="justify-content: start;">
  <img src="/assets/images/linux_file_system/mnt.svg" alt="bin" style="width: 5%; height: 5%;">
</div>  
> system admins use this directory to temporarily mount file systems, and they do it manually unlike the /media directory that does it automatically.  
Also unlike the /media that is user-specific means seperate for each user, the /mnt is system-wide and all users who have the permissoin can access it.  
  
  
<div style="justify-content: start;">
  <img src="/assets/images/linux_file_system/opt.svg" alt="bin" style="width: 5%; height: 5%;">
</div>  
> In this directory there are subdirectories and files for optional software/application that doesn't come with core OS.  
but if you download with package managers like apt or dnf they are distributed by your linux distro, so they will be considered system apps that comes with OS.  
  
> But the third-party apps they get their own subdirectories in /opt and they are self contained,  
means they have their binaries in /opt/third-party-app/bin  
and they have their libraries in /opt/third-party-app/lib  
and they have their configs in /opt/third-party-app/lib  
  
  
<div style="justify-content: start;">
  <img src="/assets/images/linux_file_system/root.svg" alt="bin" style="width: 5%; height: 5%;">
</div>  
> this is the home directory for the root user.  
NOTE: / and /root are not the same thing  
/ is the root of file-system or root directory and  
/root is home of the root user, like normal users have their home in /home/user1  
  
  
<div style="justify-content: start;">
  <img src="/assets/images/linux_file_system/tmp.svg" alt="bin" style="width: 5%; height: 5%;">
</div>  
> applications and programs in our system puts all their temporary files in the /tmp like cache. since they are temporary they all get cleared on reboot.  
  
  
<div style="justify-content: start;">
  <img src="/assets/images/linux_file_system/usr.svg" alt="bin" style="width: 5%; height: 5%;">
</div>  
> we saw in the last point of /bin that /bin just points to /usr/bin.  
it holds most of the user-space programs and data.  
in some modern linux distros (debian, ubuntu, fedora, arch linux) subdirectories like /bin, /sbin, /lib are just symlinks to /usr/bin, /usr/sbin, /usr/lib  
but not all the subdirectories are in this like config /etc and logs etc...  
  
  
<div style="justify-content: start;">
  <img src="/assets/images/linux_file_system/var.svg" alt="bin" style="width: 5%; height: 5%;">
</div>  
> it contains variable files that constently changes at runtime, like logs, cache, mail, databases etc...  
  
  

