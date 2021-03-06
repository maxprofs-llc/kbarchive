---
layout: page
title: "Q158707: DDE Destroy Window Code May Stop 0x0000001e in Windows NT 4.0"
permalink: /kb/158/Q158707/
---

## Q158707: DDE Destroy Window Code May Stop 0x0000001e in Windows NT 4.0

{% raw %}

	Article: Q158707
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kb3rdparty kbProgramming
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Code that tries to destroy a DDEML window under Windows NT 4.0 can result in an
	access violation (AV), while the same code running on Windows NT 3.51 will have
	no problems.
	
	Under Windows NT 4.0, the access violation results in the following message:
	
	  STOP 0x0000001E (0xC0000005, 0xA00FE88D, 0x00000000, 0x00000030)
	  KMODE_EXCEPTION_NOT_HANDLED Address A00FE880 has base at a0000000 - win32k.sys
	
	NOTE: The second, third, and fourth parameter may vary from system to system.
	
	CAUSE
	=====
	
	This problem was discovered when using a third party application that uses DDEML
	to communicate between the main application and a plug-in application. The DDEML
	window is destroyed after communication is completed. In the window destroy
	process, Windows NT code intercedes and cleans up DDEML-related resources, and
	then continues on with the generic window destroy. During this cleanup process
	under Windows NT 4.0, a null member eventually will be introduced that will
	result in an AV. This problem does not occur under Windows NT 3.51, because the
	code has moved to the kernel under Windows NT 4.0.
	
	
	RESOLUTION
	==========
	
	This problem was resolved by adding code to the FreeDdeConv to account for
	critical section exit when the DDEML struct is vulernable to the client side.
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT version 4.0. This
	problem was corrected in the latest Microsoft Windows NT 4.0 U.S. Service Pack.
	For information on obtaining the service pack, query on the following word in
	the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	
	Additional query words: prodnt 0x1e
	
	======================================================================
	Keywords          : kb3rdparty kbProgramming 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : winnt:4.0
	
	=============================================================================
	

{% endraw %}
