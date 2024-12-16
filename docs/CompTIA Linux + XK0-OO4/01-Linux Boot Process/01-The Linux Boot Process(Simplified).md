# Linux Boot Process(Simplified)
1. The computer starts.
2. The BIOS on the motherboard checks all of the hardware and IO devices. The boot process for the computer can begin.
3. The boot program([GRUB](02-Legacy%20GRUB.md)) will look for the section of the hard drive that contains the data needed to boot an OS.
4. This bootloader will then load the Linux Kernel.
5. The Kernel will load what is called an initial RAM disk -> It contains a bunch of device drivers and starts to load the computer's drivers to eventually mount the File System from the hard disk.
6. After the Kernel is all set up and ready to go, it then starts off the initialization system.
7. Once the initialization system starts, it takes over mounting the computer's File Systems.
8. At this point, the initial RAM disk is no longer needed and gets removed.
9. The initialization system continues to load services and gets the computer in a state where it can be used.

![](../img/Pasted%20image%2020240925113423.png)


## Boot Logs

> [!NOTE] `dmesg`
> Traditional utility used for viewing the Kernel ring buffer.


> [!NOTE] `journalctl -k`
> `systemd` utility to view the Kernel ring buffer within the `systemd` jounal.
