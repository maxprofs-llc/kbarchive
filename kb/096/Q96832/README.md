---
layout: page
title: "Q96832: Setup Stops Before Completing Upgrade"
permalink: /kb/096/Q96832/
---

## Q96832: Setup Stops Before Completing Upgrade

{% raw %}

	Article: Q96832
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:5.x,6.0,6.2,6.21
	Operating System(s): 
	Keyword(s): 
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 5.0, 5.0a, 6.0, 6.2, 6.21 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article addresses the problem of the MS-DOS Setup program stopping before
	completing the installation process. This information applies to MS-DOS 5
	Upgrade, MS-DOS 6 Upgrade, MS-DOS 6.2 Upgrade, MS-DOS 6.2 Step-Up, and MS-DOS
	6.21 Upgrade.
	
	MORE INFORMATION
	================
	
	Setup Stops Before You Create an Uninstall Disk
	-----------------------------------------------
	
	If Setup stops before you create an Uninstall disk, do the following:
	
	1. Remove any disks in the floppy disk drives and restart your computer by
	  pressing CTRL+ALT+DEL.
	
	2. Insert an unformatted disk in drive A.
	
	3. Type the following at the MS-DOS command prompt and press ENTER:
	
	  " format a: /s " (without the quotation marks)
	
	  MS-DOS formats the floppy disk in drive A and transfers system files to the
	  disk.
	
	4. Restart your computer with the floppy disk in drive A.
	
	5. Type the following at the MS-DOS command prompt and press ENTER to make sure
	  you can access your hard disk drive
	
	  " dir <drive>: " (without the quotation marks)
	
	  where <drive> is your hard disk drive. For example if your hard disk
	  drive is drive C, type the following command:
	
	  " dir c: " (without the quotation marks)
	
	6. Run Setup again. If you get a message about an incompatible partition, call
	  Microsoft Product Support Services. Do not use the SETUP /U command.
	
	Setup Stops After You Create an Uninstall Disk
	----------------------------------------------
	
	If Setup stops after you create an Uninstall disk but before Setup is 99 percent
	complete, do not run Setup again. Also, do not restart your computer using your
	previous version of MS-DOS on your hard disk drive. Instead, do the following:
	
	1. Insert the Uninstall disk in drive A.
	
	2. Restart your computer by pressing CTRL+ALT+DEL. Setup displays a dialog box.
	
	3. Press C to continue Setup.
	
	If you cannot continue Setup or if Setup stops when it is 99 percent complete,
	call Microsoft Product Support Services.
	
	Additional query words: appnote 6.00 5.00 dos 6.20 set up install instal stepup
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS621 kbMSDOS620 kbMSDOS600 kbMSDOS500 kbMSDOS500a
	Version           : MS-DOS:5.x,6.0,6.2,6.21
	
	=============================================================================
	

{% endraw %}
