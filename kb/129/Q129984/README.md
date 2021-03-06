---
layout: page
title: "Q129984: SWITCH.INF Script Unavailable as Option in Remote Access"
permalink: /kb/129/Q129984/
---

## Q129984: SWITCH.INF Script Unavailable as Option in Remote Access

{% raw %}

	Article: Q129984
	Product(s): Microsoft Windows NT
	Version(s): 3.5,4.0
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 04-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 3.5, 4.0 
	- Microsoft Windows NT Server versions 3.5, 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	You are unable to select a script from your SWITCH.INF file in the Before
	Dialing or After Dialing fields of the Remote Access (RASPHONE.EXE) Security
	Settings dialog box.
	
	CAUSE
	=====
	
	One or more scripts from SWITCH.INF may not appear as options in RASPHONE.EXE
	if:
	
	- You have not restarted RASPHONE.EXE since modifying the SWITCH.INF file.
	
	- You saved the SWITCH.INF file as a UNICODE TXT file.
	
	- You used incorrect syntax in the SWITCH.INF file.
	
	RESOLUTION
	==========
	
	If one or more scripts from SWITCH.INF do not appear as options in RASPHONE.EXE,
	follow these steps:
	
	1. Restart RASPHONE.EXE. After making any change to the SWITCH.INF file, you
	  must restart RASPHONE.EXE before the changes are available.
	
	2. Confirm that SWITCH.INF is saved as a standard TXT file. If you have saved
	  the SWITCH.INF file as a UNICODE TXT file, none of the scripts in SWITCH.INF
	  will be available in the Security Settings dialog of RASPHONE.EXE.
	  NOTEPAD.EXE has the option of saving a file as a standard TXT file or as a
	  UNICODE TXT file.
	
	3. Confirm that you used proper syntax in the SWITCH.INF file. Each script in
	  the SWITCH.INF file is designated by the name of the script enclosed in
	  square brackets (for example, [MyScript]). If the script name is not enclosed
	  in square brackets, the script will not be available in the RASPHONE.EXE
	  Security Settings dialog box.
	
	  Also, if a semi-colon precedes the script name on the same line of SWITCH.INF,
	  RASPHONE.EXE will treat the line as a comment and the script will not be an
	  option in the Security Settings dialog box.
	
	Additional query words: prodnt
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT350search kbWinNT400search kbWinNTW350 kbWinNTW350search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS350 kbWinNTS350search
	Version           : :3.5,4.0
	
	=============================================================================
	

{% endraw %}
