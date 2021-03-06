---
layout: page
title: "Q248057: How to Remove and Reinstall the Workstation Service"
permalink: /kb/248/Q248057/
---

## Q248057: How to Remove and Reinstall the Workstation Service

{% raw %}

	Article: Q248057
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kbenv kberrmsg
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes how to remove and reinstall only the Workstation service.
	
	MORE INFORMATION
	================
	
	To remove and reinstall only the Workstation service, use the following steps:
	
	1. Click Start, point to Settings, click Control Panel, and then double-click
	  Network.
	
	2. On the Services tab, click the Workstation service. Make note of the other
	  services that are installed on your computer at this time.
	
	3. Click Remove, click Yes when you receive the warning message, and then click
	  Close.
	
	4. After the bindings re-configuration tasks are complete, restart your computer
	  and log on locally with local Administrator privileges.
	
	  NOTE: You may receive a logon message stating that a domain controller for
	  your domain could not be located. If you receive this message, click OK.
	
	5. Click Start, point to Settings, click Control Panel, and then double-click
	  Network.
	
	6. Click the Services tab. Click Yes when the following message is displayed:
	
	  Windows NT networking is not installed. Do you want to install it now?
	
	7. Click the appropriate network connection (RAS or Wired connection).
	
	8. Search for your network adapter. When you are finished, click Next.
	
	9. Click the network protocol you want to use, and then click Next.
	
	10. Click the Workstation service, and then click Next.
	
	11. When the "Ready to Install" dialog box is displayed, click Next.
	
	12. Specify the location of installation media or files, and then click Next.
	
	13. When you receive a warning message stating that TCP/IP is already installed,
	  click OK.
	
	14. When you receive a warning message stating that the server already exists on
	  the system, click OK.
	
	15. When you receive a warning message stating that the NetBIOS interface
	  already exists on the system, click OK.
	
	16. You will receive similar warning messages for each of the remaining services
	  you noted in step 2 when you removed the Workstation service. Click OK when
	  you receive each warning message.
	
	17. After you finish the installation, click Next twice.
	
	18. Accept the defaults for the workgroup assignment.
	
	19. Restart the computer, and then log on to the domain as normal.
	
	You should use this procedure only as a last resort in getting the Workstation
	service to work properly. Because the Workstation service was the only service
	you removed, you receive warning messages for the other default Windows NT
	networking services that are installed during this process.
	
	During a typical network services installation, you must provide detailed
	information about the Internet Protocol (IP), subnet mask, and so on. Because
	you did not remove any other services, when the binding configurations are
	applied after the reinstallation, all prior network-related services information
	remains intact. This is why it is possible to leave the computer in a workgroup
	in the final stages of the reinstallation. The original domain membership was
	applied in the binding configuration sequence.
	
	You may have to use the procedure outlined in this article after you have
	exhausted all other options, and you may receive the following error message
	when you attempt to start the Workstation service:
	
	  The workstation service terminated with the following error: "the system
	  could not find the file specified."
	
	The following error messages are related to the Workstation service:
	
	  
	
	- Event ID: 3870
	  Source: Workstation <computername> is not a valid computer name.
	
	- Event ID: 7023
	  Source: Service Control Manager Error
	  The Workstation service terminated with the following error:
	  A duplicate name exists on the network.
	
	- Event ID: 7002
	  Source: Service Control Manager
	  The TCP/IP NetBIOS Helper service depends on the NetworkProvider group and no
	  member of this group started.
	
	Before you use the procedure outlined in this article, ensure the Windows
	Internet Naming Service (WINS) database on the network does not have an entry
	for the computer name. The procedure outlined in this article should be
	considered a last effort.
	
	REFERENCES
	==========
	
	For additional information, click the article number below to view the article
	in the Microsoft Knowledge Base:
	
	  Q197157 Workstation Service Does Not Start
	
	  Q103470 NetBIOS Name Conflicts When NetBEUI Used on Multiple NICs
	
	Additional query words:
	
	======================================================================
	Keywords          : kbenv kberrmsg 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbNTTermServ400 kbNTTermServSearch
	Version           : winnt:4.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
