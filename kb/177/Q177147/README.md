---
layout: page
title: "Q177147: Default for Use Locally Cached Profile Dialog"
permalink: /kb/177/Q177147/
---

## Q177147: Default for Use Locally Cached Profile Dialog

{% raw %}

	Article: Q177147
	Product(s): Microsoft Windows NT
	Version(s): WINDOWS:2000; winnt:4.0 SP4
	Operating System(s): 
	Keyword(s): kbFEA kbWinNT400sp4fea
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 SP4 
	- Microsoft Windows NT Server version 4.0 SP4 
	- Microsoft Windows 2000 Server 
	- Microsoft Windows 2000 Professional 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about editing the registry.
	Before you edit the registry, make sure you understand how to restore it
	if a problem occurs. For information on how to do this, view the "Restoring
	the Registry" online Help topic in Regedit.exe or the "Restoring a Registry
	Key" online Help topic in Regedt32.exe.
	
	SUMMARY
	=======
	
	Windows NT Service Pack 4 includes a new feature that in the System Policy
	Editor will allow the administrator to define the default selection for the
	prompt displayed to the user in the event a slow network is detected and a
	locally cached user profile exists. This fix requires that the service pack be
	applied to both the server and client workstation.
	
	MORE INFORMATION
	================
	
	Windows NT 4.0 displays a prompt to the user when a slow network has been
	detected asking if the locally cached profile should be used to avoid the amount
	of time it may take to download a user profile over a modem connection, for
	example. Prior to Service Pack 4, this prompt defaulted to the action of using
	the locally cached profile and there was no way to change this default. A new
	addition has been made to the template files that create the options available
	in the System Policy Editor that allows the administrator to set this default to
	download the user profile from the server or to use the locally cached profile.
	
	With the addition of the newest Userenv.dll, the changes can be applied directly
	to the registry.
	
	WARNING: Using Registry Editor incorrectly can cause serious problems that may
	require you to reinstall Windows. Microsoft cannot guarantee that problems
	resulting from the incorrect use of Registry Editor can be solved. Use Registry
	Editor at your own risk.
	
	For information about how to edit the registry, view the "Changing Keys And
	Values" online Help topic in Registry Editor (Regedit.exe) or the "Add and
	Delete Information in the Registry" and "Edit Registry Data" online Help topics
	in Regedt32.exe. Note that you should back up the registry before you edit it.
	
	1. Start Registry Editor (Regedt32.exe).
	
	2. Add the following value to the registry:
	
	  HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Winlogon
	
	  Value: SlowLinkProfileDefault
	  Type: REG_DWORD
	  Value: 0 or 1
	
	  1 = Download Profile
	  0 = Use Local Profile
	
	The default for Windows NT 4.0 is 1
	The default for Windows 2000 is 0
	
	Additional query words: spe poledit roving roam
	
	======================================================================
	Keywords          : kbFEA kbWinNT400sp4fea 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400search kbWinNT400search kbwin2000Serv kbWinNTW400sp4 kbWinNTSsearch kbWinNTS400sp4 kbWinNTS400search kbwin2000ServSearch kbwin2000Search kbwin2000ProSearch kbwin2000Pro
	Version           : WINDOWS:2000; winnt:4.0 SP4
	Hardware          : x86
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
