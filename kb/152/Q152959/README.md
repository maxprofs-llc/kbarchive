---
layout: page
title: "Q152959: XADM: How to Remove the First Exchange Server in a Site"
permalink: /kb/152/Q152959/
---

## Q152959: XADM: How to Remove the First Exchange Server in a Site

{% raw %}

	Article: Q152959
	Product(s): Microsoft Exchange
	Version(s): 4.0,5.0,5.5
	Operating System(s): 
	Keyword(s): kbusage exc4 exc5 exc55
	Last Modified: 07-MAR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 4.0, 5.0, 5.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article outlines the steps necessary to remove the first Microsoft Exchange
	Server computer installed in an Exchange Server site.
	
	In addition to any mailboxes and public folders, by default the first server in a
	site contains and is responsible for the site folders. Site folders consist of
	the Offline Address Book (OAB) folder, the Schedule+ Free Busy Information
	folder, and the Organizational Forms folder, if one exists. Other servers
	installed in the site rely, by default, on the first server for this
	information. For example, in order for the third server in the site to generate
	the OAB, it must make a connection to the first server. If you remove the first
	server in the site without performing the steps in this article, the data
	contained in these site folders may be inaccessible or lost.
	
	The first server in the site is also, by default, the routing calculation server.
	The routing calculation server is responsible for updating the site's Gateway
	Address Routing Table (GWART). You also must reassign this responsibility before
	you remove the first server from the site. For additional information about
	doing this, click the article number below to view the article in the Microsoft
	Knowledge Base:
	
	  Q162012 XADM: Unable to Change the Routing Calculation Server
	
	If you have removed the first server in the site before reading this article,
	click the article number below to view the article in the Microsoft Knowledge
	Base:
	
	  Q152960 XADM: Reassigning Site Roles after Removing the First Server in an
	  Exchange Site
	
	IMPORTANT: If the first server in the site is also the Key Management (KM) Server
	and you follow the procedure in this article, you may later have issues when you
	try and install KM services on another server in the site. For additional
	information, click the article number below to view the article in the Microsoft
	Knowledge Base:
	
	  Q196161 XADM: Cannot Install Key Management Server in Site
	
	MORE INFORMATION
	================
	
	Before you remove the first Exchange Server computer in the site, perform the
	following steps to avoid issues:
	
	IMPORTANT: If there are any users or public folders (non-site) homed on this
	Exchange Server computer, you must move the mailboxes to another server in the
	site, and you must replicate any public folders to other servers in the site, to
	ensure that you do not lose data. Please refer to the Microsoft Exchange Server
	Administrator Guide, chapters 12 and 15, for more information.
	
	Offline Address Book::
	
	1. Choose a server in the site to contain the OAB.
	
	2. Click the Public Information Store object, and then click Properties.
	
	3. Click the Instances tab.
	
	4. In the Public Folders list, click to select Offline Address Book and OAB
	  Version 2 (if applicable), and then click Add. This creates a replica of
	  these folders on the server you chose in step 1.
	
	5. Click OK.
	
	6. Using the Exchange Server Administrator program, click the Configuration
	  container, and open the properties of the DS Site Configuration object.
	
	7. In the Offline Address Book Server list, click the server you chose in step
	  1.
	
	Schedule+ Free Busy Information and Organizational Forms::
	
	1. Choose a server in the site to contain the Schedule+ information and the
	  organizational forms.
	
	2. Using the Exchange Server Administrator program, click the Configuration
	  container, click the Servers container, and then click the server you chose
	  in step 1.
	
	3. Click the Public Information Store object, and then click Properties.
	
	4. Click the Instances tab.
	
	5. In the Public Folders list, click to select Schedule+ Free Busy Information
	  and Organization Forms, and then click Add. This creates a replica of these
	  folders on the server you chose in step 1.
	
	6. Click OK.
	
	This creates an instance for the Schedule+ Free Busy Information folder. The
	original Schedule+ Free Busy Information public folder is removed when the first
	server is removed, and the new instance becomes active.
	
	Routing Calculation Server::
	
	1. Choose a server in the site to be the new routing calculation server.
	
	2. Using the Exchange Server Administrator program, click the Configuration
	  container, and then double-click the Site Addressing object.
	
	3. Click the General tab.
	
	4. In the Routing Calculation Server list, click the server you chose in step 1.
	  You must make some other change in the properties pages to activate the Apply
	  button, so that the changes are retained.
	
	5. Click the Routing tab, and then click Recalculate Routing.
	
	6. Click OK.
	
	7. Finally, follow the steps in the following article:
	
	  Q189286 XADM: How to Delete a Server from a Site
	
	NOTE: Microsoft recommends that the first server in the site be powered off or
	unplugged from the network temporarily after you perform the above steps to
	verify that you have completed this procedure successfully. After you verify
	that the changes work (start a Microsoft Exchange client, and verify that you
	can access the Schedule+ free and busy information of another user and can
	generate an Offline Address Book), leave the first server off the network, or
	powered off, make sure that there are no entries in the Windows Internet Naming
	System (WINS) or Domain Name System (DNS) for the server you are removing, and
	then perform the following steps to permanently remove this server from the
	site:
	
	1. Using the Exchange Server Administrator program, click the Configuration
	  container, and then click the Servers container.
	
	2. Click the first server in the site.
	
	3. On the Edit menu, click Delete, or press the DELETE key.
	
	NOTE: The Microsoft Exchange Schedule+ Free/Busy Connector does NOT move
	automatically and is deleted when the first server is removed from the site. If
	this happens, recreate this object by following the steps in the following
	article in the Microsoft Knowledge Base:
	
	  Q148199 XCLN: Re-creating a Deleted Schedule+ Free/Busy Agent
	
	To Include Schedule+ Free Busy Information::
	
	The Schedule+ Free Busy Information site folder is repopulated as users log on to
	Schedule+ and generate changes. During this period some users' free and busy
	information is temporarily unavailable.
	
	Until a user logs on and makes an appointment (a "busy" time) there is no free
	and busy information to view.
	
	For additional information, click the article numbers below to view the articles
	in the Microsoft Knowledge Base:
	
	  Q235898 XADM: Cannot Generate Offline Address Book
	
	  Q284148 XADM: How to Remove the Last Exchange Server 5.5 Computer from an
	  Exchange 2000 Administrative Group
	
	  Q260781 XADM: Change Mode Button Inactive in Organization Properties Dialog
	  Box After Upgrading Exchange 5.5 Service Pack 3 to Exchange 2000 Server
	
	  Q189286 XADM: How to Delete a Server from a Site
	
	Additional query words: ies
	
	======================================================================
	Keywords          : kbusage exc4 exc5 exc55 
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbExchange400 kbZNotKeyword2
	Version           : :4.0,5.0,5.5
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
