
## Create Virtual Machine on the MAC laptops for use within the 4.01 laboratory.

### INTRODUCTION

Your studies/research here may require you to use a PC to develop software.  
Currently we have a number of Macintosh laptops that natively provide the OS-X operating system.  
Sometimes, we want to use an alternate O/S like Linux (Ubuntu) to develop within.
Os-X has a program called VirtualBox, by Oracle, that allows these alternate OS's to be installed and run within the OS-X environment.

This document describes the procedure to create a Virtual Machine to the installation of ```Ubuntu 16.04 LTS Desktop``` onto the MACs.  

It is assumed that:  
- your Mac has installed OS-X El Capitan
- you have at least 200G free on the internal HDD

### PROGRAM INSTALL
```
You need to have the program called "VirtualBox" by "Oracle" installed.
Download and install this, if it is not already installed.
Currently we use v5.2.6
```
### CREATE NEW VIRTUAL MACHINE
```
Start the VirtualBox program

Click "New" to create a new VM

Set the name of the VM, this creates a directory of the same name.
Set the OS to "Linux"
Set the OS2 to "Ubuntu 64-bit"

-> Next

For the memory, select approx 75% of the total available memory.
The Laptop used to create this doc has 12G, so I choose 8G to be assigned to the VM when it is running.
This allows some 4G of memory for the MAC to also utilise while the VM is running.

-> Next

You will be asked to select what kind of Virtual HDD to be used.
Select VDI.

Select VDI again,
Select FIXED size, as we assume that this gives a performance increase.
set the size to 80G, as we know that when all the tools/programs are installed, we need this amount of room.
-> Next.

it takes approx 25mins to format/prepare the VDI (Virtual Disk).

Following that, the new VM will near appear within the VirtualBox GUI.

To prepare the blank VM with a guest OS link Ubuntu, perform the following:
```
### Install an OS on the blank VM
```
To install Ubuntu on the blank VM, do the following:

Insert the installer-DVD into the MAC,
MAC will respond that the disk is unreadible -> select IGNORE.

Within the VirtualBox program,
right-click on the VM that was created using this procedure,
and navigate to START, then to NORMAL.

A dialog will appear,
tell the VirtualBox to source the guest OS from the Virtual Optical Disk labelled "DVD" or similar.
Then select "Start".

```
### Connect external devices into the VM
```
External devices like USB-Sticks, USB-232-convertors, etc
can be connected to the MAC and by default these external devices
are NOT mapped into the Virtual Machine.

To map an external device into the VM, do the following:

1. connect the external USB device to the MAC,
so that the MAC can see it.
1. within VirtualBox, single click the VM you would like the external USB device to appear
1. within VirtualBox, single click "Settings" up the top.
1. ports -> USB -> USB Device Filters
1. single click the greep "plus" symbol
1. select the external USB device that you want mapped in.  
For the Nexys board, choose the device from Digilent.
1. click OK

The external USB device should now be mapped into the selected VM.  
If not, remove the external device from the MAC, and reinsert. 
Type "dmesg" at the prompt (within Ubuntu) to debug.
```


