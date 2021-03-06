---
layout: page
title: "Q231799: XCON: MIME Messages Sent Using Outlook Express Receive an NDR"
permalink: /kb/231/Q231799/
---

## Q231799: XCON: MIME Messages Sent Using Outlook Express Receive an NDR

{% raw %}

	Article: Q231799
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5
	Operating System(s): 
	Keyword(s): exc55 EXC55SP3Fix
	Last Modified: 30-SEP-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	An originator who sends a MIME message with Outlook Express through an
	administrative management domain (ADMD) to an Exchange Server 5.5 SP1 computer
	receives a non-delivery report (NDR). The following events are also logged in
	the application event log:
	
	  Event ID: 290
	  Type: Warning
	  Description: NDR generated, reason code unable-to-transfer and diagnostic code
	  content-syntax-error.
	
	  Event ID: 62
	  Type: Warning
	  Description: A delivery failure occurred to the message...
	
	  Event ID: 210
	  Type: Warning
	  Description: Content conversion from 56010A01 (P2-88) to 2A864886F7140501
	  (MDBEF).
	
	CAUSE
	=====
	
	This behavior is due to problems in the way that Exchange Server handles general
	text body parts.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Exchange Server
	version 5.5. For additional information, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q191014 XGEN: How to Obtain the Latest Exchange Server 5.5 Service Pack
	
	The English version of this fix should have the following file attributes or
	later:
	
	Component: Message Transfer Agent (MTA)
	
	+---------------------------+
	| File name    | Version    | 
	+---------------------------+
	| Address.dll  | 5.5.2590.0 | 
	+---------------------------+
	| Dbserver.sch | N/A        | 
	+---------------------------+
	| Dcprods.cat  | N/A        | 
	+---------------------------+
	| Ems_rid.dll  | 5.5.2590.0 | 
	+---------------------------+
	| Emsmta.exe   | 5.5.2590.0 | 
	+---------------------------+
	| Info4log.cfg | N/A        | 
	+---------------------------+
	| Infoblog.cfg | N/A        | 
	+---------------------------+
	| Infodlog.cfg | N/A        | 
	+---------------------------+
	| Infollog.cfg | N/A        | 
	+---------------------------+
	| Infoplog.cfg | N/A        | 
	+---------------------------+
	| Infotlog.cfg | N/A        | 
	+---------------------------+
	| Mmiext.dll   | 5.5.2590.0 | 
	+---------------------------+
	| Mtacheck.exe | 5.5.2590.0 | 
	+---------------------------+
	| Mtamsg.dll   | 5.5.2590.0 | 
	+---------------------------+
	| P2.xv2       | N/A        | 
	+---------------------------+
	| X400om.dll   | 5.5.2590.0 | 
	+---------------------------+
	| X400omv1.dll | 5.5.2590.0 | 
	+---------------------------+
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 5.5. This problem was first corrected in Exchange Server 5.5 Service
	Pack 3.
	
	Additional query words:
	
	======================================================================
	Keywords          : exc55 EXC55SP3Fix 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : winnt:5.5
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
