---
layout: page
title: "Q319127: Services Do Not Start and Event ID 7022 Is Logged"
permalink: /kb/319/Q319127/
---

## Q319127: Services Do Not Start and Event ID 7022 Is Logged

{% raw %}

	Article: Q319127
	Product(s): Microsoft Windows NT
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kberrmsg
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	You may experience the following symptoms:
	
	- When you start your computer, you may receive a message that states that one
	  or more services did not start.
	
	- If other users try to access your computer over the network, they may not be
	  able to locate your computer.
	
	- The following event ID message may be logged in the System log in Microsoft
	  Event Viewer:
	
	  Event ID: 7022
	  Source: Service Control Manager
	  Type: Error
	  Description: Server service hung on startup.
	
	CAUSE
	=====
	
	This issue may occur if the Spooler service tries to start before the Server
	service. This issue may occur if you installed either the Lexmark International
	Markvision (LexBce) service or the Hewlett-Packard JetAdmin port monitoring
	software on your computer.
	
	RESOLUTION
	==========
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	To resolve this issue, edit the registry to make the Spooler service dependant on
	the Server service. If you do so, the Spooler service does not start until the
	Server service is running.
	
	To create this dependency:
	
	1. Click Start, and then click Run.
	
	2. In the Open box, type "regedt32" (without the quotation marks), and then
	  click OK.
	
	3. Locate and click the following registry key:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Spooler
	
	4. Click Add Value on the Edit menu.
	
	5. Type "DependOnService" (without the quotation marks) in the Value Name box.
	
	6. Click REG_MULTI_SZ in the Data Type box, and then click OK.
	
	7. Type "LanmanServer" (without the quotation marks) in the Data box, and then
	  click OK.
	
	8. Click Exit on the Registry menu to quit Registry Editor.
	
	9. Restart your computer.
	
	MORE INFORMATION
	================
	
	For information about how to contact Lexmark International or Hewlett-Packard,
	click the appropriate article number below to view the article in the Microsoft
	Knowledge Base:
	
	  Q65416 Hardware and Software Third-Party Vendor Contact List, A-K
	
	  Q60781 Hardware and Software Third-Party Vendor Contact List, L-P
	
	  Q60782 Hardware and Software Third-Party Vendor Contact List, Q-Z
	
	The third-party contact information included in this article is provided to help
	you find the technical support you need. This contact information is subject to
	change without notice. Microsoft in no way guarantees the accuracy of this
	third-party contact information.
	
	The third-party products discussed in this article are manufactured by vendors
	independent of Microsoft; we make no warranty, implied or otherwise, regarding
	these products' performance or reliability.
	
	Additional query words:
	
	======================================================================
	Keywords          : kberrmsg 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : :4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
