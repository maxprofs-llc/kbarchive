---
layout: page
title: "Q106228: There Is Not Enough Free Space on..."
permalink: /kb/106/Q106228/
---

## Q106228: There Is Not Enough Free Space on...

{% raw %}

	Article: Q106228
	Product(s): Microsoft Disk Operating System
	Version(s): 6.2,6.22
	Operating System(s): 
	Keyword(s): 
	Last Modified: 21-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 6.2, 6.22 
	-------------------------------------------------------------------------------
	
	This information applies to both Microsoft DoubleSpace and Microsoft
	DriveSpace. For MS-DOS 6.22, use DRVSPACE in place of DBLSPACE for commands
	and filenames.
	
	SYMPTOMS
	========
	
	When you try to resize a DoubleSpace-compressed drive, you may receive one of
	the following messages (when drive C is compressed):
	
	  DoubleSpace cannot change the size of drive C.
	  There is not enough free space on drive C to complete this operation. Delete
	  some unnecessary files from drive C and try again.
	
	  -or-
	
	  DoubleSpace cannot change the size of drive <H>.
	  There is not enough free space on your original startup drive, which is now
	  drive <H>. DoubleSpace will need at least <0.XX> MB of free space
	  on that drive. Delete some files from that drive, and try this operation
	  again.
	
	where <H> is your host drive and <0.XX> is the free minimum space
	needed on your host drive.
	
	CAUSE
	=====
	
	The first error message is incorrect and can occur if you specify too little
	free space to be left available on the host drive. For example, if your drive C
	is compressed and you type "dblspace /size /reserve=0.00 c:" (without the
	quotation marks) at the MS-DOS command prompt and then press ENTER, you receive
	this error.
	
	Although the second error message is accurate, you may not be able to delete
	enough files from the host drive to allow the resize process to succeed.
	
	RESOLUTION
	==========
	
	The minimum free space you can leave on the host drive (for a boot drive) varies
	depending on the size of your AUTOEXEC.BAT and CONFIG.SYS files; however, a
	general rule is approximately 0.4 megabytes. If drive C is compressed and you
	want to leave the minimum space free on the host drive, type "dblspace /size
	/reserve=0.4 c:" (without the quotation marks) at the MS-DOS command prompt and
	then press ENTER.
	
	If you receive the second error message noted above, DoubleSpace cannot resize
	your drive due to the large size of your AUTOEXEC.BAT, CONFIG.SYS, or
	DBLSPACE.INF file. Use the following procedure to resize your
	DoubleSpace-compressed drive:
	
	1. Rename CONFIG.SYS to CONFIG.PSS. For example, type "ren c:\config.sys
	  config.pss" (without the quotation marks) at the MS-DOS command prompt and
	  then press ENTER.
	
	  WARNING: If your CONFIG.SYS file contains references to device drivers that
	  are needed to access your hard disk drive, do not rename your CONFIG.SYS
	  file.
	
	2. Rename AUTOEXEC.BAT to AUTOEXEC.PSS.
	
	3. Reboot your computer and then resize your DoubleSpace-compressed drive.
	
	4. If you still cannot resize your DoubleSpace-compressed drive:
	
	   - Copy your DBLSPACE.INF file to DBLSPACE.PSS.
	
	   - Edit your DBLSPACE.INF file and remove any comments or other lines you
	     don't need.
	
	   - Reboot your computer and then resize your DoubleSpace-compressed drive.
	
	   - Copy DBLSPACE.PSS over the DBLSPACE.INF you modified. For example, type
	     "copy c:\dos\dblspace.pss c:\dos\dblspace.inf" (without the quotation
	     marks) at the MS-DOS command prompt and then press ENTER.
	
	5. Rename CONFIG.PSS to CONFIG.SYS.
	
	6. Rename AUTOEXEC.PSS to AUTOEXEC.BAT
	
	7. Reboot your computer so that the original AUTOEXEC.BAT and CONFIG.SYS files
	  are processed.
	
	To avoid this problem in the future, leave more free space on your host drive.
	For example, to reserve one megabyte of free space, type "dblspace /size
	/reserve=1 c:" (without the quotation marks) at the MS-DOS command prompt and
	then press ENTER.
	
	MORE INFORMATION
	================
	
	DoubleSpace copies the following files to the host drive so that it can continue
	resizing the drive if the power fails during the resize process:
	
	  AUTOEXEC.000              ; copy of C:\AUTOEXEC.BAT
	  CONFIG.000                ; copy of C:\CONFIG.SYS
	  DBLSPACE.EXE              ; copied from C:\DOS
	  DBLSPACE.HLP              ; copied from C:\DOS
	  DBLSPACE.INF              ; copied from C:\DOS
	  DBLSPACE.WIN              ; file to keep track of Windows
	  DEFRAG.EXE                ; copied from C:\DOS
	
	If your AUTOEXEC.BAT, CONFIG.SYS, and/or DBLSPACE.INF files have grown
	significantly since you resized your DoubleSpace-compressed drive to its minimum
	size, you may not be able to resize the drive. If your DBLSPACE.INF file has not
	changed, you need 339,646 bytes free on your host drive, plus the size of your
	CONFIG.SYS and AUTOEXEC.BAT files.
	
	NOTE: Using the DoubleSpace command-line switches, you can set the minimum free
	space to be left on the host drive to .13 megabytes less than you can using the
	user interface of the DoubleSpace maintenance program.
	
	Additional query words: 6.20
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS622 kbMSDOS620
	Version           : :6.2,6.22
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
