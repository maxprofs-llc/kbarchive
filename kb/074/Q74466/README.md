---
layout: page
title: "Q74466: UNDELETE Does Not Work If File Deleted from Windows or Shell"
permalink: /kb/074/Q74466/
---

## Q74466: UNDELETE Does Not Work If File Deleted from Windows or Shell

{% raw %}

	Article: Q74466
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:5.0,5.0a,6.0,6.2,6.21,6.22
	Operating System(s): 
	Keyword(s): 
	Last Modified: 21-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 5.0, 5.0a, 6.0, 6.2, 6.21, 6.22 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	With the MIRROR deletion tracking program loaded (for example, MIRROR /TC),
	UNDELETE does not work if the deletion has been done through Windows or MS-DOS
	Shell File Manager. This deletion tracking program, which is a TSR
	(terminate-and-stay-resident program), cannot detect the deleted files because
	Windows and Shell delete files through ROM instead of standard interrupts.
	
	When MIRROR is installed, it tracks which files have been deleted. When UNDELETE
	/DT is run, MIRROR can recover all available clusters in the deleted file.
	However, when a file is deleted inside MS-DOS Shell, the file is not added to
	the list of deleted files. For this reason, UNDELETE /DT does not work (inside
	Shell or from DOS) if the file has been deleted in Shell.
	
	The only way to undelete the file is to use the /DOS switch on the UNDELETE
	command.
	
	MORE INFORMATION
	================
	
	If a file has been deleted in Windows or Shell, and you want to undelete it,
	shell out of Windows or MS-DOS Shell and issue the following command:
	
	  UNDELETE <filename> /DOS
	
	The /DOS switch recovers only those files that are internally listed as deleted
	by MS-DOS 5.0. If a deletion-tracking file exists, this switch causes UNDELETE
	to ignore it. Because the deletion tracking is ignored, the first character of a
	filename used to mark as available for reuse will not be retrievable. "UNDELETE
	<filename/s> /DOS" will prompt you for the first character of the
	filename.
	
	Do not use Windows or MS-DOS Shell File Manager to delete or undelete. Exit
	Windows or Shell and carry out the command from the C prompt. UNDELETE will not
	work by shelling out from Windows or Shell even though the deletion tracking
	program is installed prior to running Windows or Shell.
	
	Additional query words: 6.22 5.00 5.00a 6.00 6.20
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS621 kbMSDOS622 kbMSDOS620 kbMSDOS600 kbMSDOS500 kbMSDOS500a
	Version           : MS-DOS:5.0,5.0a,6.0,6.2,6.21,6.22
	
	=============================================================================
	

{% endraw %}
