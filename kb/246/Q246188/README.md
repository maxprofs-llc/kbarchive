---
layout: page
title: "Q246188: Err Msg: This Feature Is Not Available in This Version of..."
permalink: /kb/246/Q246188/
---

## Q246188: Err Msg: This Feature Is Not Available in This Version of...

{% raw %}

	Article: Q246188
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0 SP3,4.0 SP4,4.0 SP5,4.0 SP6
	Operating System(s): 
	Keyword(s): kbenv kberrmsg kbnetwork
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 4.0 SP3, 4.0 SP4, 4.0 SP5, 4.0 SP6 
	- Microsoft Windows NT Server, Enterprise Edition versions 4.0 SP4, 4.0 SP5, 4.0 SP6 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	While you are trying to form a network adapter team (also known as an adapter
	fault-tolerant team) with an Intel Pro 100 Intelligent Server adapter, the
	following error message may be displayed on Windows NT 4.0 Server:
	
	  This feature is not available for this version of Windows NT Terminal Server
	
	This message may be displayed even though you are forming the fault-tolerant team
	on Windows NT 4.0 Server, not Terminal Server.
	
	CAUSE
	=====
	
	The utility that is used to form the team looks for an entry named "Terminal
	Server" in the registry at the following location:
	
	  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\
	
	If this key is found, the error message is displayed and the formation of the
	adapter fault-tolerant team is not allowed, even if you are not using Terminal
	Server.
	
	WORKAROUND
	==========
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	As a workaround, you can back up and then delete the key listed above. After the
	key is deleted, you can form the adapter fault-tolerant team. After you form the
	team, you can add the registry key back.
	
	NOTE: None of the information in this article applies to Windows NT 4.0, Terminal
	Server Edition. No changes should be made to a Windows NT 4.0 Terminal Server
	based on this article.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.
	
	MORE INFORMATION
	================
	
	The Terminal Server registry key is added by the installation of some programs
	that can also be installed in Terminal Server, such as Microsoft Office.
	
	Support for network adapter fault tolerance was made available after Window NT
	4.0 Service Pack 3. Windows NT 4.0 does not directly provide support for this
	feature, but it is provided by some manufacturers of network adapters. This
	feature is not available in Terminal Server. For more information, and a list of
	manufacturers that provide network adapter fault tolerance, see the following
	Microsoft Knowledge Base article:
	
	  Q171415 Network Adapter Fault Tolerance for Windows NT 4.0
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbenv kberrmsg kbnetwork 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400sp6 kbWinNTSEnt400sp5 kbWinNTSEnt400sp4 kbWinNTS400sp6 kbWinNTS400sp5 kbWinNTS400sp4 kbWinNTS400sp3 kbWinNTS400search
	Version           : winnt:4.0 SP3,4.0 SP4,4.0 SP5,4.0 SP6
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
