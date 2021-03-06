---
layout: page
title: "Q195985: XADM: Move Mailbox Fails with Client Operation Failed Error"
permalink: /kb/195/Q195985/
---

## Q195985: XADM: Move Mailbox Fails with Client Operation Failed Error

{% raw %}

	Article: Q195985
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5
	Operating System(s): 
	Keyword(s): exc55sp2fix exc55
	Last Modified: 22-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you move a user in the Microsoft Exchange Server Administrator program, the
	move may fail and the following error message is displayed.
	
	  Client Operation Failed 80004005-0501-80004005
	
	CAUSE
	=====
	
	The data in the mailbox is moved through a buffer in memory. If a property's
	data straddled a buffer, there was a chance that the property would be changed
	to PT_NULL and memory allocated for the property could not be freed.
	
	This caused the failure in move user.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Exchange Server
	version 5.5. For more information, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q191014 XGEN: How to Obtain the Latest Exchange Server 5.5 Service Pack
	
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Component: Information Store
	
	  File Name    Version
	  -----------------------
	  Gapi32.dll   5.5.2435.0
	  Mdbmsg.dll   5.5.2435.0
	  Store.exe    5.5.2435.0
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server 5.5
	Service Pack 1.
	
	Additional query words:
	
	======================================================================
	Keywords          : exc55sp2fix exc55 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : winnt:5.5
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
