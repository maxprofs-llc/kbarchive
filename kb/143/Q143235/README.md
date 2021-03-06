---
layout: page
title: "Q143235: XADM: Error Message: Error -550 Has Occurred"
permalink: /kb/143/Q143235/
---

## Q143235: XADM: Error Message: Error -550 Has Occurred

{% raw %}

	Article: Q143235
	Product(s): Microsoft Exchange
	Version(s): winnt:4.0,5.0,5.5
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 12-MAY-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 4.0, 5.0, 5.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If the computer running Microsoft Exchange Server stops responding or is not
	shut down gracefully after stopping all the services properly, the following
	error message may appear on screen and in the event logs:
	
	  Error -550 has occurred
	
	This message may also appear when you start the directory or information store
	service, in case of a power failure.
	
	CAUSE
	=====
	
	This error usually means that the database is in an inconsistent state and
	cannot start.
	
	NOTE: This problem usually occurs when users move or delete their log files or
	database. If the log files are deleted or moved, recovery appears to work (no
	log files = no recovery), but the database will be inconsistent. If the database
	is moved, recovery will not work (the path to the database is hard-coded in the
	log files). If the log files are moved without updating the registry, recovery
	will not work.
	
	RESOLUTION
	==========
	
	Confirm that the state of the database is inconsistent, and then try a
	defragmentation repair. Be sure to stop all services and back up all files
	before you run the Edbutil.exe program.
	
	1. Check the state of the database.
	
	Versions 4.0 and 5.0
	--------------------
	
	Use Edbutil.exe with the "MH" option on the problem database, and dump the output
	to a text file:
	
	  EDBUTIL /MH c:\exchsrvr\dsadata\dir.edb >c:\edbdump.txt
	
	-OR-
	
	  EDBUTIL /MH c:\exchsrvr\mdbdata\priv.edb >c:\edbdump.txt
	
	-OR-
	
	  EDBUTIL /MH c:\exchsrvr\mdbdata\pub.edb >c:\edbdump.txt
	
	Version 5.5
	-----------
	
	Use Eseutil.exe with the "MH" option on the problem database, and dump the output
	to a text file:
	
	  ESEUTIL /MH c:\exchsrvr\dsadata\dir.edb >c:\edbdump.txt
	
	-OR-
	
	  ESEUTIL /MH c:\exchsrvr\mdbdata\priv.edb >c:\edbdump.txt
	
	-OR-
	
	  ESEUTIL /MH c:\exchsrvr\mdbdata\pub.edb >c:\edbdump.txt
	
	2. Edit the Edbdump.txt file and confirm that the state of the database is
	  inconsistent.
	
	3. If the database is inconsistent, run the following commands:
	
	Versions 4.0 and 5.0
	--------------------
	
	  EDBUTIL /R /DS
	
	Version 5.5
	-----------
	
	  ESEUTIL /R /DS
	
	Use EDBUTIL /IS or ESEUTIL /IS to recover the Priv.edb and Pub.edb files. They
	both use the same log files, so they will be recovered together.
	
	
	Additional query words: exfaq winnt XSRVDS exfaqad 0xFFFFFDDA JET_errDatabaseInconsistent 4294966746
	
	======================================================================
	Keywords          : kbusage 
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbExchange400 kbZNotKeyword2
	Version           : winnt:4.0,5.0,5.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
