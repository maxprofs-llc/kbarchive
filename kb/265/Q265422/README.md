---
layout: page
title: "Q265422: How RDISK.EXE Updates Repair Information"
permalink: /kb/265/Q265422/
---

## Q265422: How RDISK.EXE Updates Repair Information

	Article: Q265422
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes how the RDISK.EXE utility updates repair information.
	
	MORE INFORMATION
	================
	
	The following changes occur to the repair directory when you update the repair
	information:
	
	1. System._ is deleted.
	
	2. $$Hive$$.tmp is created. (This is the system hive being regenerated.)
	
	3. Some DC##.tmp files are generated in the user's Home directory. If the user
	  does not have a Home directory, the files are generated on the root directory
	  of the partition. There will be five DC##.tmp files created and then deleted
	  for each new hive that is generated.
	
	4. $$Hive$$.tmp is compressed and called System._.
	
	5. Software._ is deleted.
	
	6. $$Hive$$.tmp is created. (This is the software hive being regenerated.)
	
	7. $$Hive$$.tmp is compressed and called Software._.
	
	8. Ntuser.da_ is deleted.
	
	9. $$Hive$$.tmp file is created. (This is the default user profile being
	  generated by copying Winnt\Profiles\Default user\Ntuser.dat.)
	
	10. $$Hive$$.tmp is compressed and called Ntuser.da_. (All other files remain
	  untouched unless rdisk -s is used; in that case, Sam._ and Security._ are
	  also replaced.)
	
	11. You are prompted to make an Emergency Repair Disk (ERD).
	
	12. If you reply Yes, all the files in the repair directory are copied to the
	  ERD.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : winnt:4.0
	Issue type        : kbinfo
	
	=============================================================================
	