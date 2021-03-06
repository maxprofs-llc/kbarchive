---
layout: page
title: "Q270133: XADM: Exchange Notes Connector Loses Notes Address"
permalink: /kb/270/Q270133/
---

## Q270133: XADM: Exchange Notes Connector Loses Notes Address

{% raw %}

	Article: Q270133
	Product(s): Microsoft Exchange
	Version(s): 5.5 SP3
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 SP3 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	A Lotus Notes user may not be able to reply to an e-mail message that is sent
	from an Exchange Server user by means of a Microsoft Exchange Connector for
	Lotus Notes.
	
	CAUSE
	=====
	
	This problem can occur when an Exchange Server user sends mail to a Notes user
	because the Exchange Notes Connector derives the sender's Notes proxy address
	from the user's Exchange Server display name. The Exchange Notes Connector
	erroneously removes the space (0x20) and horizontal tab (0x09) characters from
	the address when the Exchange Notes Connector creates the Notes address from the
	Exchange Server display name; therefore, some double-byte character set (DBCS)
	characters (for example, 0x5909 and 0x5a20) that contain 0x20 or 0x09 in Unicode
	are also removed. The sender's Notes address cannot be replied to because of
	this loss of characters.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Exchange Server 5.5.
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q191014 How to Obtain the Latest Exchange Server 5.5 Service Pack
	
	The Japanese version of this fix should have the following file attributes or
	later:
	
	Component: Exchange Notes Connector
	
	+------------------------------------------------------------------------+
	| File name  | Version    | Date        | Time    | File Size | Platform | 
	+------------------------------------------------------------------------+
	| Mapi32.dll | 5.5.2653.6 | 24-Aug-2000 | 3:30:31 | 870,160   | Intel    | 
	+------------------------------------------------------------------------+
	| Mapi32.dll | 5.5.2653.6 | 24-Aug-2000 | 3:24:50 | 1,385,232 | Alpha    | 
	+------------------------------------------------------------------------+
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Exchange Server version 5.5
	Service Pack 3. This problem was first corrected in Exchange Server 5.5 Service
	Pack 4.
	
	
	
	Additional query words: MAPI32 UNICODE 0x09 0x20 Space Tab BYTE WORD
	
	======================================================================
	Keywords          :  
	Technology        : kbExchangeSearch kbZNotKeyword2 kbExchange550SP3
	Version           : :5.5 SP3
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
