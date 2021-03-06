---
layout: page
title: "Q260204: XWEB: Access Denied Error Message When Installing Outlook Web Ac"
permalink: /kb/260/Q260204/
---

## Q260204: XWEB: Access Denied Error Message When Installing Outlook Web Ac

{% raw %}

	Article: Q260204
	Product(s): Microsoft Exchange
	Version(s): 5.0,5.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Active Server Components, version 5.0 
	- Microsoft Outlook Web Access, version 5.5 Service Packs 1, 2, 3 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	When you install or reinstall Outlook Web Access (OWA) you may receive the
	following error message:
	
	  Access Denied Microsoft Windows NT ID no: 0xc0020005
	
	The following event may also be logged in the application event log of the
	Windows NT Event Viewer.
	
	  Event ID: 14, Source: W3SVC, description: "exchfilt.dll could not be loaded."
	
	CAUSE
	=====
	
	This error message can occur if a folder or file is corrupted. It can also be
	the result of a locked file, a lack of appropriate permissions, or a service
	that does not stop or start.
	
	RESOLUTION
	==========
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	Because there is more than one possible cause for this error message, to resolve
	this issue perform the following steps (these are steps that have resolved this
	issue in the past):
	
	1. Stop any unnecessary services. These include, but are not limited to:
	  antivirus software, backup software, and any third-party Internet-related
	  services.
	
	2. In the Exchange Server Administrator program, make sure that the permissions
	  for the Organization, Site, and Site Configuration containers are sufficient.
	  Generally there is an Administrator account that has Permissions
	  Administrator rights and a Site Service account that has Service Account
	  Administrator rights. Make sure that there are no unnecessary entries, such
	  as a user or group that has Search rights.
	
	3. Make sure that you are logged on with an account that has Administrator
	  rights to the domain and at least Permissions Administrator rights in
	  Exchange Server. (To test permissions, try to stop and start the World Wide
	  Web Publishing service manually.)
	
	4. Look for an Exchsrvr\Webdata folder. If one exists, back up any customized
	  Active Server Pages (ASP) files, and then delete this folder.
	
	5. Locate a Exchsrvr\Webtemp folder; if one exists, delete it.
	
	6. Locate the following registry key:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSExchangeWEB
	
	  If this key exists, back the key up, and then use Registry Editor to delete
	  the key.
	
	7. Locate the following registry key:
	
	  HKEY_LOCAL_MACHINE\Software\Microsoft\Exchange\Setup\Web Connector
	
	  If this key exists, back the key up, and then use Registry Editor to delete
	  the key.
	
	8. Use the Add/Remove option in your Exchange Server Setup program to reinstall
	  Outlook Web Access.
	
	MORE INFORMATION
	================
	
	For additional information, click the article numbers below to view the articles
	in the Microsoft Knowledge Base:
	
	  Q246270 XADM: Access Denied Error When Installing a Service Pack on Exchange
	  Server 5.5 with OWA
	
	  Q170472 XADM: Access Denied Error When Starting Exchange Administrator
	
	
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbOutlookSearch kbZNotKeyword6 kbExchangeSearch kbZNotKeyword2 kbOWASearch kbOWA550SP1 kbOWA550SP2 kbOWA550SP3 kbExchangeActiveServComp500
	Version           : :5.0,5.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
