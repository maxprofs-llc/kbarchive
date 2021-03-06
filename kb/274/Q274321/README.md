---
layout: page
title: "Q274321: XADM: Key Management Server Does Not Start with Event ID 5389"
permalink: /kb/274/Q274321/
---

## Q274321: XADM: Key Management Server Does Not Start with Event ID 5389

{% raw %}

	Article: Q274321
	Product(s): Microsoft Exchange
	Version(s): 5.5 SP3
	Operating System(s): 
	Keyword(s): 
	Last Modified: 04-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 SP3, used with:
	   - the operating system: Microsoft Windows 2000 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After you upgrade a domain controller on which Exchange Server 5.5 is installed
	from Microsoft Windows NT Server 4.0 to Microsoft Windows 2000 Server, Key
	Management server (KM server) may not start and the following informational and
	error messages may be logged:
	
	  Event Type: Information
	  Event Source: MSExchangeKMS
	  Event Category: None
	  Event ID: 5389
	  Date: 9/13/2000
	  Time: 5:56:06 PM
	  User: N/A
	  Computer: THE
	  Description:
	  Microsoft Exchange Key Management service is exiting with return code 0.
	
	  Event Type: Information
	  Event Source: ESE97
	  Event Category: General
	  Event ID: 101
	  Date: 9/13/2000
	  Time: 5:56:06 PM
	  User: N/A
	  Computer: THE
	  Description:
	  MSExchangeKMS (2480) The database engine stopped.
	
	  Event Type: Error
	  Event Source: MSExchangeKMS
	  Event Category: None
	  Event ID: 5015
	  Date: 9/13/2000
	  Time: 5:56:05 PM
	  User: N/A
	  Computer: THE
	  Description:
	  Microsoft Exchange Key Management service failed logging on as a MAPI client.
	
	CAUSE
	=====
	
	This issue can occur because when you upgrade a server that is a domain
	controller from Windows NT Server 4.0 to Windows 2000 Server, the domain is
	removed and then re-intialized with Active Directory, and the Exchange Server
	service account loses membership to the local Administrators group.
	
	RESOLUTION
	==========
	
	To resolve this issue:
	
	1. In the Active Directory Users and Computers Microsoft Management Console
	  (MMC) snap-in, click the Users container, and then double-click the service
	  account user.
	
	2. Click the Member Of tab.
	
	3. Make sure that the service account is a member of the Domain Administrators
	  group.
	
	4. If the service account is member of the Domain Users group only, click Add,
	  and then add the Domain Administrators group to the membership list.
	
	MORE INFORMATION
	================
	
	This issue can also occur with the Exchange Server Internet Mail Service. For
	additional information, click the article number below to view the article in
	the Microsoft Knowledge Base:
	
	  Q262939 XADM: Internet Mail Service Does Not Start After Demoting and
	  Re-Promoting Windows 2000 Server Domain Controller
	
	Additional query words: KMS Win2k DCpromo demote AD IMS
	
	======================================================================
	Keywords          :  
	Technology        : kbExchangeSearch kbZNotKeyword2
	Version           : :5.5 SP3
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
