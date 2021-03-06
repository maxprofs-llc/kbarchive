---
layout: page
title: "Q164463: XADM: User Names Missing from the Recipients Container"
permalink: /kb/164/Q164463/
---

## Q164463: XADM: User Names Missing from the Recipients Container

{% raw %}

	Article: Q164463
	Product(s): Microsoft Exchange
	Version(s): winnt:4.0,5.0,5.5
	Operating System(s): 
	Keyword(s): kbusage exc4 exc5 exc55
	Last Modified: 20-MAY-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 4.0, 5.0, 5.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After you restore the information store of a Microsoft Exchange Server computer
	from a backup and join an existing site, you may not see any users in the
	server's Recipients container.
	
	You may, however, see the recipient resources in the server's Private Information
	Store Mailbox Resources property page.
	
	RESOLUTION
	==========
	
	NOTE: These steps use the DS/IS consistency adjuster. For additional information
	about the rehoming effects that may occur if you use this tool, click the
	article number below to view the article in the Microsoft Knowledge Base:
	
	  Q182979 XADM: Function and Effects of Running the DS/IS Consistency Adjuster
	
	To resolve this problem in Microsoft Exchange Server 5.0:
	
	NOTE: If the original mailboxes were located on another container, this container
	must first be re-created before performing the steps below.
	
	1. Start DS/IS consistency adjuster as follows:
	
	Select the server name under the Servers container, and then on the File menu
	click Properties, click Advanced, then click Consistency Adjuster.
	
	2. Make sure that Synchronize with the directory in the Information Store
	  properties is selected, and then click the All Inconsistencies option button
	  and click Adjust.
	
	3. Confirm that all the user names are now present in the recipient container.
	
	To resolve this problem in Microsoft Exchange Server 5.0:
	
	NOTE: If the original mailboxes were located on another container, this container
	must first be re-created before performing the steps below.
	
	1. Start DS/IS consistency adjuster as follows:
	
	  Select the server name under the Servers container, then click Properties on
	  the File menu, and click Advanced.
	
	2. Make sure that the Directory and Information Store check boxes are selected,
	  and then select the All Inconsistencies radio button and click Adjust.
	
	3. Confirm that all the user names are now present in the recipient container.
	
	To resolve this problem in Microsoft Exchange Server 4.0:
	
	- Follow the same procedure as above, unless any of the mailboxes are contained
	  in the subcontainers. In that case, you must first manually re-create each
	  mailbox (using exactly the same DN) before you start the DS/IS consistency
	  adjuster.
	
	For additional information on manually re-creating the mailboxes, click the
	article number below to view the article in the Microsoft Knowledge Base:
	
	  Q154491 XADM: DS/IS Fails to Re-create Mailboxes in Subcontainers
	
	Additional query words:
	
	======================================================================
	Keywords          : kbusage exc4 exc5 exc55 
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbExchange400 kbZNotKeyword2
	Version           : winnt:4.0,5.0,5.5
	
	=============================================================================
	

{% endraw %}
