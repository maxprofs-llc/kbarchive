---
layout: page
title: "Q133730: Network User Profiles Not Supported on Real-Mode Networks"
permalink: /kb/133/Q133730/
---

## Q133730: Network User Profiles Not Supported on Real-Mode Networks

{% raw %}

	Article: Q133730
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 04-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Server-based user profiles do not work on a computer running only a real- mode
	network client.
	
	CAUSE
	=====
	
	You must use a 32-bit network client and a network operating system that
	supports the creation of home directories to use server-based user profiles.
	
	RESOLUTION
	==========
	
	Install a 32-bit protected-mode network client.
	
	MORE INFORMATION
	================
	
	You can store user profiles (user-specific information) on a local computer or a
	network server. Using user profiles allows multiple users to use a single
	computer and retain their individual settings, or to log on to the network from
	any computer and use the same desktop settings.
	
	Storing user profiles on a network server requires:
	
	- 32-bit protected-mode client services that support automatic download and
	  update of user profiles.
	
	- A network operating system that supports the creation of home directories.
	  The protected-mode client network services included with Windows 95 download
	  and update user profiles from the following directories:
	
	   - Microsoft Client for Microsoft Networks:
	
	  \\primary domain controller\user's home directory
	
	   - Microsoft Client for NetWare Networks:
	
	  \\preferred server\sys\mail\user_id
	
	The following conditions are supported when you are using user profiles on a
	network:
	
	- Profiles stored on a Windows NT 3.x server on workstations running the
	  Microsoft Client for Microsoft Networks.
	
	- Profiles stored on a Novell NetWare server, with Windows 95-based
	  workstations running the Microsoft Client for NetWare Networks.
	
	- Profiles stored on other network operating systems that support the creation
	  of home directories and supply their own 32-bit client services.
	
	REFERENCES
	==========
	
	Microsoft Windows 95 "Resource Kit," pages 477-489
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbWin95search kbZNotKeyword3
	Version           : :
	
	=============================================================================
	

{% endraw %}
