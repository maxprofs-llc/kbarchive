---
layout: page
title: "Q247782: XCON: Mail Slow Across Connectors, with Event IDs 3120 and 9316"
permalink: /kb/247/Q247782/
---

## Q247782: XCON: Mail Slow Across Connectors, with Event IDs 3120 and 9316

{% raw %}

	Article: Q247782
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	When you administer Microsoft Exchange Server 5.5, you may notice that mail
	transfer across connectors is extremely slow. Event Viewer may record the
	following events in the application log:
	
	  Event ID: 3120
	  Source: MSExchangeMTA
	  Type: Warning
	  Description: A resource limit has been reached when attempting to open an
	  association. Number of sessions configured: 30
	
	  Event ID: 9316
	  Source: MSExchangeMTA
	  Type: Warning
	  Description: An RPC communications error occurred. No data was sent over the
	  RPC connection. Locality table (LTAB) index: x. Windows NT error: 9317.
	
	CAUSE
	=====
	
	This behavior can occur when the Message Transfer Agent (MTA) experiences a
	resource shortage.
	
	RESOLUTION
	==========
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	To resolve this behavior, change the 'Concurrent XAPI sessions' value in the
	registry:
	
	1. Start Registry Editor (Regedt32.exe).
	
	2. Locate the following key in the registry:
	
	HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSExchangeMTA\Parameters\ 
	
	3. Double-click the Concurrent XAPI Sessions value.
	
	4. In the Radix area click Hex, in the Data box type "50" (without the quotation
	  marks), and then click OK.
	
	NOTE: By default this value is set to 50 hex (80 decimal). If Performance
	Optimizer is run with default settings selected, the value will be set to 30.
	
	5. Quit Registry Editor.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : winnt:5.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
