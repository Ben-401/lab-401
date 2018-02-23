
## Installation instructions for ```Ubuntu 16 LTS``` for use within the 4.01 laboratory.

### INTRODUCTION

Your studies/research here may require you to use a PC to develop software.  
To facilitate a common development environment,
it is recommended that each computer have installed the same O/S, programs and user settings.

This document describes the installation procedure to install ```Ubuntu 16 LTS Desktop``` onto a PC (or VM).  
It then describes a method to update the O/S.

It is assumed that:  
- you have a PC that meets the minimum requirements for the installation. Refer to “www.ubuntu.com” for these details.  
- Your HDD is blank, or is OK to overwrite all data  
- The install DVD is labelled “Ubuntu 16.04”.  
- Your computer has a connection to the internet (for updates during install)  

### INSTALLATION INSTRUCTIONS
```
BIOS:  
	recommended to "Load defaults", "Set time", "Set boot order to DVD->HDD", etc

Boot from the DVD, and follow the instructions below.
NOTE that some MACs may say that "Disk is not readible" -> press Ignore.

Welcome  
	ensure "English"
	select "Install Ubuntu"

Preparing to install Ubuntu  
	it is recommended to "Download updates while installing"  
	it is recommended NOT to "install this third-party software"  
	-> Continue  

Installation Type  
	either select  
	+ "Erase disk and install Ubuntu"
		this will create and install onto a SINGLE partition,
		it is best for the installation within a VM.
	+ "Something Else" - allows you to manually delete and create partitions.  
		this is best when installing on a HDD within a PC-BOX.
		A suggested partition scheme is:  

			PART	DEV	MNT	SIZE	FSTYPE	NOTES
			Pri	sda1	/boot	  1G	EXT4		100m - 1000m
			L	sda5	/swap	16G	linux-swap	2x ram capacity
			L	sda6	/	60G	EXT4		ubuntu+xilinx=30G, so double it
			L	sda7	/usr	10G	EXT4		2-10g
			L	sda8	/var	10G	EXT4		2-10g
			L	sda9	/tmp	32G	EXT4		2x swap
			L	sda10	/home	??G	EXT4		rest of the disk
NOTE that the SIZEs listed above are recommended if your HDD is >= 320G, adjust acordingly.  
	write the changes -> Yes

	then "Continue" with the setup installation.  

Where are you  
	select "Adelaide"   
	-> Continue  

Select Keyboard type  
	(automatically selected as English US/English US)  
	on the VM, you may need to adjust the HORIZ-size to be able to see all the buttons.
	-> Continue  

Your Details:  
	Fill in the details, considering the comments below  
Your Name	put FirstName LastName (shown at login-screen)  
Comp Name	this is used as the laptops hostname/machinename, set it accordingly  
		ie: remove your 'real name' from the 'computer name'  
username	use your FAN ie: abcd1234 (for consistency on the Flinders network)  
password	recommended to choose a unique password (not your FAN password)  
password	as above, must match  

	It is recommended to set the following  
		unselected	log in automatically  
		selected	require password to login  
		  unselected	encryption  

	-> Begin Install

The installation from DVD takes about 20 minutes.  
Following the installation, remove DVD and press 'Return'. PC will reboot.  

Ubuntu 16.04 should boot-up to the login screen.  
```

### Configuration

```
Your name should appear on the login screen. To login, type your 'password' and press enter.  

The desktop will load.  

(32-bit only)Shortly after, a dialog “Incomplete Language Support” may appear. Dismiss this,.  

(32-bit only) The time may be incorrect, ignore this for now as a system update will fix this.  
```

### Perform a System Update to Ubuntu 16.10 (as of 22-FEB-2018)  

```
Connect to the internet  

Start an x-term (command line interface)  
	the top icon on the left hand side is 'search'. Do a search and type "term".  
	The search results will find a number of programs, choose "Terminal".  

Update/upgrade
	in the xterm window, type/perform the following commands:  
	sudo apt-get update  
	sudo apt-get upgrade  

	during the above commands, you will be required to authorise about 300MB download, so select 'y' when asked.  

Reboot your computer, and re-run the above two commands:  
	sudo apt-get update  
	sudo apt-get upgrade  
This should result in an up-to-date system at least to Ubuntu 16.10.  


```

### optional programs to install

```
git					source code control software
unity-tweak-tool			program to tweak/modify the desktop behaviour
compizconfig-settings-manager	program to tweak/modify the desktop behaviour
mc					midnight commander file browser (text based)
openssh-server			used to ssh into a host installation

```

