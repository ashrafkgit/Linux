Every time you power on your Linux PC, it goes through a series of stages before finally displaying a login screen that prompts for your username or password. 
There are 4 distinct stages that every Linux distribution goes through in a typical boot-up process.

![image](https://github.com/ashrafkgit/Linux/assets/134578702/5c99fc65-6345-4274-87e2-1ebc03483f79)

In this page, we will highlight the various steps taken by the Linux OS from the time it is powered on to the time you log in. 

Kindly note that this page only takes into consideration the GRUB2 bootloader and systemd init as they are currently in use by a vast majority of modern Linux distributions.


The booting process takes the following 4 steps that we will discuss in greater detail:

**BIOS** Integrity check (**POST**)

Loading of the Boot loader (**GRUB2**)

Kernel initialization

Starting **systemd**, the parent of all processes

## 1. The BIOS Integrity Check (POST)

The boot process is usually initialized when a user presses the power-on button – if the PC was already shut down – or reboots the system using either the GUI or on the command line.

When the Linux system powers up, the BIOS (Basic Input Output System) kicks in and performs a Power On Self Test (POST). This is an integrity check that performs a plethora of diagnostic checks.
