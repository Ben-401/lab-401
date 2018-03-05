
## Installation instructions for "Xilinx ISE 14.7", in particular "WebPACK".

### INTRODUCTION

Your studies/research here may require you to use the Xilinx tools to develop software.  
This document describes the installation procedure to install "Xilinx ISE 14.7 (WebPACK)" onto a PC.  
It then describes a method to run and configure the software.

It is assumed that:
1.  you have a PC that meets the minimum requirements for the installation.  
Refer to "www.xilinx.com" for those details.
1.  You have Ubuntu 16.04 (or equivalent) installed.  
1.  You have the 4x Xilinx installer files shown below (there are 2x DVDs in the 4.01 Lab).  

### INSTALLATION INSTRUCTIONS

get four files  
```c
Xilinx_ISE_DS_14.7_1015_1­1.tar  
Xilinx_ISE_DS_14.7_1015_1­2.zip.xz  
Xilinx_ISE_DS_14.7_1015_1­3.zip.xz  
Xilinx_ISE_DS_14.7_1015_1­4.zip.xz
```
make a $temp$ directory  
put the four xilinx files listed above into the $temp$ directory  
cd into that $temp$ directory  
untar the TAR file, leave the three other XZ files alone  
```tar xvf Xilinx_ISE_DS_14.7_1015_1­1.tar```  
run the installer with root privledges  
```sudo ./xsetup```  
A graphical installer will appear.  

Welcome  
-> Next  

Select Download Installation directory  
choose the location of the three XZ-data-files (should be the $temp$ directory previously created)  
-> Next  

Xilinx Software Setup  
the integrity of the files will be verified  
-> Please wait 2mins approx  

Accept Licence Agreements (1 of 2)  
Select both checkboxes  
-> Next  

Accept Licence Agreement (2 of 2)  
Select the checkbox  
-> Next  

Select Products To Install  
Select "ISE WebPACK" (approx 17-23 Gb required)  
-> Next  

Select Installation Options  
Select "Use multiple CPU cores..." (if applicable)  
Deselect "Acquire or manage a licence..." (see below)  
Select "Ensure Linux System..."  
"WebTalk" is greyed-out  
Deselect "Install Cable Drivers" (see below)  
NOTE: We manage the licence after installation.  
NOTE: Cable Drivers are not required for our Nexys4DDR project,
as we download the generated bitstream to the fpga via a method not involving JTAG.  
-> Next  

Select Destination Directory  
a good option is "/opt/Xilinx" for the installation.  
ignore "Import Tool Preferences from Previous Versions" because there
shouldnt be any previous versions on a fresh install of ubuntu.  
-> Next  

Installation Options Summary  
-> Install  

Installation takes approx 15 mins.  
-> Finish  

The $temp$ directory could now be deleted, but wait until you read the bit about licence files.  
You may want to keep the four install files.  

### RUNNING INSTRUCTIONS
To run the "Xilinx ISE", you first need to 'source' the settings script.  
Two options are:  
1. open an xterm,  
execute "cd /opt/Xilinx/14.7/ISE_DS/"  
execute "source settings[32|64].sh"  
execute "ise &"  
or  
1. create a script that can be executed from the desktop to run the above commands.  
Contents of the "run_ise.sh" would be:  
```
#!/bin/bash
source /opt/Xilinx/14.7/ISE_DS/settings64.sh
ise &
```
a suitable location for this file would either be in:  
"/opt/Xilinx/14.7/ISE_DS/" or "$HOME".  

Assuming that you copied the provided "run_ise.sh" file into your home directory,  
you will then need to set executable flag permissions  
```chmod u+x run_ise.sh```  

Now you can optionally place a shortcut on the desktop or the applications menu ("Dash Panel") to run the "run_ise.sh" script. For example, in `/usr/share/applications`, create a `.desktop` file (i.e. `xilinx_ise.desktop`) and insert the following (changing the paths accordingly to your installation):
```
[Desktop Entry]
Type=Application
Terminal=false
Name=Xilinx ISE
Icon=/opt/Xilinx/14.7/ISE_DS/ISE/data/images/pn-ise.png
Exec=/home/mega65/run_ise.sh
```
This will add the program to the applications menu. When running, you can then pin it to the sidebar ("Launcher"): right-click > `Lock to Launcher`. You can also put this file on the Desktop (`/home/mega65/Desktop`).

When ISE is first launched, a dialog will appear advising of a "Xilinx Licence Error".  
This is expected so dismiss this dialog.  

A "Xilinx Licence Configuration manager" dialog will appear.  
This can be dismissed/closed.  

At this stage of the installation, ISE can be used to open a project and navigate through a design.
Instructions on how to use ISE are not contained in this file.  

At this stage, ISE *cannot* be used to completely compile and generate a bitstream, because the
installation has not been supplied with a valid licence (see below for licence details).  
ISE *will* be able to 'synthesize'.  

### LICENCE FILE INSTALLATION
For ISE to compile source-code and generate a bitstream, a Xilinx Licence File is required.  
Xilinx offers a free licence for use with ISE WebPACK.  
Optionally, use the "Xilinx.lic" file on the Lab-401-DVDs.  

To attain a licence file, you need a 'Xilinx' login account (see below).  
To get a licence file, you need to register on the Xilinx.com website.  
Go to the web address:  
xilinx.com/getlicense  
Login using your xilinx user/pass  
goto somewhere like "Get Licence", and fill in your details.  
NOTE that this section ofg the doco needs to be updated...  
A "Product Licencing" page will appear with your details.  
Check your details, note the "Corporate Email" is where the Licence-file will be emailled.  

Once you have a licence file ("Xilinx.lic"), put that file into the home-directory of the machine that ISE is installed onto.  

Using ISE, Help -> Manage Licence... ->  
 -> Manage Licences... -> Load Licence... -> browse to  

and select the "Xilinx.lic" file -> Open -> ISE should respond with "Licence installation was successful".  

You can now safely delete the "Xilinx.lic" file as the ISE software has read your licence file, and stored a copy in the "~/.Xilinx" directory.  
NOTE that one "Xilinx.lic" file has been seen to be able to make-licensed multiple ISE installations.  


