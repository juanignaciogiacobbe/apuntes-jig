# Grand Unified Boot Loader(GRUB) 
1. When you first boot up your computer, the BIOS checks everything out.
2. Once the BIOS has determined that all hardware is good to go, it will then locate a bootloader.
3. **Stage 1 of the GRUB boot process**: The GRUB bootloader has a small image file called `boot.img` that exists within the master boot record, which is the first 512 Bytes of your physical hard disk. This hard disk is going to be the one that is marked with the boot flag.
4. The purpose of the `boot.img` file is to get the `core.img` file loaded. This file exists with an empty space towards the beginning of your boot disk.
5. The purpose of the `core.img` file is to locate the actual boot partition of the system.
6. **Stage 2 of the GRUB boot process**: Where the actual boot partition gets read. 
	- Within the `/boot/grub` directory on a legacy GRUB system, the GRUB program is looking for either a `grub.conf`(Where you are going to find the most Red Hat based distributions) file or a `menu.lst`(Where you are going to find the most Debian based distributions) file.
	- The other file that is necessary is the `device.map` file, which indicates which drive contains the actual Kernel and the OS that needs to be booted. Once this file is read, the Linux Kernel gets loaded by GRUB, and the rest of the system boots up.

![](../img/Pasted%20image%2020240925120818.png)

## GRUB Shell

> [!NOTE] `grub`
> Invokes the GRUB shell environment.


> [!NOTE] `help`
> Print the help listing for GRUB, or get more info on a command, i.e `help [command]`.


> [!NOTE] find
> Search for a file in all partitions and list the device(s) the file is on.


> [!NOTE] quit
> Exit the grub shell.


