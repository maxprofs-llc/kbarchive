---
layout: page
title: "Q34908: Determining Physical Drive Numbers"
permalink: /kb/034/Q34908/
---

## Q34908: Determining Physical Drive Numbers

{% raw %}

	Article: Q34908
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:3.x,4.x,5.0,5.0a,6.0,6.2,6.21,6.22
	Operating System(s): 
	Keyword(s): 
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 3.1, 3.2, 3.21, 3.3, 3.3a, 4.0, 4.01, 5.0, 5.0a, 6.0, 6.2, 6.21, 6.22 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	There is some confusion about determining the physical drive number of a floppy
	drive for use with DRIVPARM or DRIVER.SYS. The first drive is floppy drive A,
	referred to as physical drive 0. Floppy drive B is referred to as physical drive
	1. On systems that do not have a physical drive B, MS-DOS creates a logical
	entry for it (in the drive parameter table) that maps back to floppy drive A.
	This allows systems with only one floppy drive to copy files from one floppy
	disk to another by referring to the one drive as both drive A and drive B.
	
	On systems with an XT-class ROM BIOS, there are two additional floppy drives,
	physically numbered 2 and 3, that can be available. On IBM PC AT and PS/2-class
	ROM BIOS systems, there are only two floppy drives available.
	
	Additional query words: 6.22 3.x 4.00 5.00 5.00a 6.00 6.20 6.21
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS321 kbMSDOS400 kbMSDOS320 kbMSDOS330a kbMSDOS621 kbMSDOS622 kbMSDOS620 kbMSDOS600 kbMSDOS310 kbMSDOS500 kbMSDOS330 kbMSDOS401 kbMSDOS500a
	Version           : MS-DOS:3.x,4.x,5.0,5.0a,6.0,6.2,6.21,6.22
	
	=============================================================================
	

{% endraw %}
