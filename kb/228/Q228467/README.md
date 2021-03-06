---
layout: page
title: "Q228467: Access Violation in Lsass.exe When Passing a Null Pointer"
permalink: /kb/228/Q228467/
---

## Q228467: Access Violation in Lsass.exe When Passing a Null Pointer

{% raw %}

	Article: Q228467
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kbWinNT4sp6fix
	Last Modified: 16-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	- Microsoft Windows NT Server, Enterprise Edition version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Lsass.exe may cause an access violation when you run third-party security
	programs that attempt denial of service attacks. After the access violation, you
	cannot log on locally and the administrative tools that rely on Local Security
	Authority (LSA) or LSARPC do not function correctly.
	
	CAUSE
	=====
	
	The NetUserEnum API enumerates all of the user, machine, and group accounts from
	a security account manager (SAM) database. This function calls an internal API
	passing a NULL value for one of the parameters. This null value causes the
	access violation in Lsass.exe.
	
	
	RESOLUTION
	==========
	
	Windows NT Server or Workstation 4.0
	------------------------------------
	
	To resolve this problem, obtain the latest service pack for Windows NT 4.0 or the
	individual software update. For information on obtaining the latest service
	pack, please go to:
	
	- http://www.microsoft.com/Windows/ServicePacks/
	
	-or-
	
	- Q152734 How to Obtain the Latest Windows NT 4.0 Service Pack
	
	For information on obtaining the individual software update, contact Microsoft
	Product Support Services. For a complete list of Microsoft Product Support
	Services phone numbers and information on support costs, please go to the
	following address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	
	Windows NT Server 4.0, Terminal Server Edition
	----------------------------------------------
	
	To resolve this problem, obtain the latest service pack for Windows NT Server
	4.0, Terminal Server Edition. For additional information, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q152734 How to Obtain the Latest Windows NT 4.0 Service Pack
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article. This problem was first corrected in
	Windows NT Server version 4.0, Terminal Server Edition Service Pack 6.
	
	Additional query words: sp4
	
	======================================================================
	Keywords          : kbWinNT4sp6fix 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400 kbWinNTS400search kbWinNTS400 kbNTTermServ400 kbNTTermServSearch
	Version           : winnt:4.0
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
