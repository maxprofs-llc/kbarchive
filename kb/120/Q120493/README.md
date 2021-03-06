---
layout: page
title: "Q120493: NWLink with Ethernet_II Frame Type Corrupt Packets"
permalink: /kb/120/Q120493/
---

## Q120493: NWLink with Ethernet_II Frame Type Corrupt Packets

{% raw %}

	Article: Q120493
	Product(s): Microsoft Windows NT
	Version(s): 3.1,3.11,3.5,4.0
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 07-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 3.1, 3.5, 4.0 
	- Microsoft Windows NT Workstation versions 3.1, 3.5, 4.0 
	- Microsoft Windows NT Advanced Server, version 3.1 
	- Microsoft Windows for Workgroups version 3.11 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A Windows for Workgroups 3.11 client can experience data corruption if you use
	IPX/SPX Compatible Transport with NetBIOS and an Ethernet_II (DIX) frame type to
	connect it to any of these network servers:
	
	- Windows for Workgroups 3.11 (ie: a peer server)
	
	- Windows NT Server version 3.5
	
	- Windows NT Workstation version 3.5
	
	- Windows NT version 3.1
	
	- Windows NT Advanced Server version 3.1
	
	After you log on to the server, incorrect file information appears when you
	attempt to do a NET USE from an MS-DOS prompt or try to connect to the server
	from File Manager.
	
	This problem occurs only when the Windows for Workgroups version 3.11 client was
	installed from the Windows NT Server version 3.5 CD-ROM.
	
	CAUSE
	=====
	
	Incorrect file information appears because the NWLINK.386 component for Windows
	for Workgroups version 3.11 is not handling the Ethernet_II (DIX) packet
	correctly.
	
	WORKAROUND
	==========
	
	To work around this problem:
	
	- Use DirectHost IPX instead of IPX/SPX Compatible Transport with NetBIOS.
	
	  -or-
	
	- Use a Frame type other than Ethernet_II, for example, 802.3 Ethernet.
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT and Windows NT
	Advanced Server version 3.1, and Windows NT Workstation and Server versions 3.5,
	3.51, and 4.0. We are researching this problem and will post new information
	here in the Microsoft Knowledge Base as it becomes available.
	
	
	Additional query words: prodnt wfw wfwg nwlink
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT350search kbWinNT400search kbWinNTW350 kbWinNTW350search kbWinNTW310 kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS350 kbWinNTS310 kbWinNTAdvSerSearch kbWinNTAdvServ310 kbWinNTS350search kbWinNTS310search kbAudDeveloper kbWinNT310Search kbWinNTW310Search kbWFWSearch kbWFW311
	Version           : :3.1,3.11,3.5,4.0
	
	=============================================================================
	

{% endraw %}
