---
layout: page
title: "Q145767: Problems Accessing Shared CD-ROM"
permalink: /kb/145/Q145767/
---

## Q145767: Problems Accessing Shared CD-ROM

{% raw %}

	Article: Q145767
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): 3.1,3.11
	Operating System(s): 
	Keyword(s): win95
	Last Modified: 10-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	- Microsoft Windows for Workgroups versions 3.1, 3.11 
	- Microsoft Windows versions 3.1, 3.11 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you try to view files on or set up programs from a shared CD-ROM drive on
	the network, you may experience one or more of the following symptoms:
	
	- You may receive "File not found" error messages.
	
	- The server or the client may stop responding (hang).
	
	- The server or the client may exit to an MS-DOS prompt.
	
	- You may not be able to view all the files in one or more folders on the
	  CD-ROM although you do not receive any error messages.
	
	These symptoms may occur even though the CD-ROM files can be viewed and accessed
	correctly from the computer that is sharing the CD-ROM drive.
	
	CAUSE
	=====
	
	This behavior can occur if the CD-ROM being shared is not fully ISO 9660
	compliant, the computer sharing the CD-ROM drive is using a real-mode Mscdex.exe
	device driver with a file version of 2.25 (or earlier), and the Mscdex.exe
	device driver is being started with the /S parameter to allow the CD-ROM drive
	to be shared on the network.
	
	RESOLUTION
	==========
	
	Share the CD-ROM drive from a computer running Microsoft Windows NT Workstation
	or Server version 3.5 (or later), or from a computer running Windows 95 using
	the 32-bit Compact Disk File System driver (Cdfs.vxd).
	
	MORE INFORMATION
	================
	
	The real-mode Mscdex.exe driver is compliant with ISO 9660, which does not allow
	for directory entries that span sectors. Therefore, excess bytes at the end of
	each directory sector are zero-filled. Mscdex.exe requires at least one of these
	zero-byte fillers at the end of each directory sector in order to traverse the
	shared CD-ROM directory on a network server.
	
	If a CD-ROM is mastered with disk authoring tools that do not comply completely
	with the ISO 9660 specification, a file may be written to the CD- ROM with a
	directory entry that is in perfect alignment with a sector boundary on the disk,
	not allowing for at least one zero-byte filler at the end of the directory
	sector.
	
	The Windows NT Workstation and Server version 3.5 and Windows 95 32-bit compact
	disk file systems allow the sharing of non-ISO 9660-compliant CD- ROMS.
	
	Additional query words:
	
	======================================================================
	Keywords          : win95 
	Technology        : kbAudDeveloper kbWin3xSearch kbWin95search kbWFWSearch kbZNotKeyword3 kbWin310 kbWin311 kbWFW310 kbWFW311
	Version           : :3.1,3.11
	
	=============================================================================
	

{% endraw %}
