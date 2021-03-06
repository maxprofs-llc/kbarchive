---
layout: page
title: "Q159182: XCON: MTAs Unable to Establish X.400 Connection"
permalink: /kb/159/Q159182/
---

## Q159182: XCON: MTAs Unable to Establish X.400 Connection

{% raw %}

	Article: Q159182
	Product(s): Microsoft Exchange
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 09-APR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Microsoft Exchange message transfer agents (MTAs) may not be able to establish a
	connection when the MTA that is being called (hereafter referred to as the
	called MTA) has a password defined in the X.400 Connector's override page.
	
	This password matches the one that is defined for the called MTA at the MTA that
	initiates the connection (hereafter referred to as the calling MTA). Messages
	destined to the called MTA will not be sent and will eventually time out, in
	which case a non-delivery report (NDR) is generated. With the default MTA
	diagnostics logging (NONE), the calling MTA will log for each connection attempt
	the following warning in the Windows NT event log:
	
	  Event ID: 48
	  Source: MSExchangeMTA
	  Category: Security
	  An error occurred authenticating credentials from the remote entity
	  /O=DIETERR/OU=ROCKLAND/CN=CONFIGURATION/CN=CONNECTIONS/CN=ROCKKITE. [2007 MTA
	  XFER-IN 23 42] (14)
	
	The called MTA does not log any entry in the Windows NT event log.
	
	CAUSE
	=====
	
	The MTA passwords exchanged during connection establishment might not match. The
	called MTA uses the password as specified on the MTA General tab instead of the
	one specified in the X.400 Connector's Override page. If these passwords are
	different, the wrong password is sent in the RT Open Accept Packet to the
	calling MTA and connection fails.
	
	WORKAROUND
	==========
	
	To work around this problem:
	
	- Do not define different passwords in the MTA General tab and the X.400
	  Connector' s Override property page at the called MTA.
	
	If for any reasons different passwords must be used, there is no workaround.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 4.0. This problem was corrected in the latest Microsoft Exchange 4.0
	U.S. Service Pack. For information on obtaining the service pack, query on the
	following word in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	
	MORE INFORMATION
	================
	
	Successful X.400 connection establishment of two MTAs requires not only the
	calling MTA to provide its MTA name and password, the called MTA has to send an
	RT Open Accept Packet that contains its MTA name and its password. Both sides
	must have the correct values defined to allow for a successful connection.
	
	NOTE: The problem described in this article only occurs if the called MTA has
	different passwords defined on its MTA General tab and the X.400 Connector' s
	property page. If the calling MTA has different passwords defined in its
	property pages the connection will be established and messages can be
	transmitted.
	
	
	Additional query words: X.400 Event ID 48 X400
	
	======================================================================
	Keywords          :  
	Technology        : kbExchangeSearch kbExchange400 kbZNotKeyword2
	Version           : winnt:4.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
