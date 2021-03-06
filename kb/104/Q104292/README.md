---
layout: page
title: "Q104292: How to Identify 128-Bit Windows 95 Dial-Up Networking Client"
permalink: /kb/104/Q104292/
---

## Q104292: How to Identify 128-Bit Windows 95 Dial-Up Networking Client

{% raw %}

	Article: Q104292
	Product(s): Windows for Workgroups and Windows NT Networking Issues
	Version(s): WINDOWS:; Win2000:95
	Operating System(s): 
	Keyword(s): kbnetwork dun win95 kbDialUp
	Last Modified: 28-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	- Microsoft Windows 98 
	- Microsoft Windows 98 Second Edition 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The Microsoft Dial-Up Networking 1.3 Upgrade includes the ability for Dial-Up
	Networking (DUN) clients to connect to a Microsoft Windows NT Remote Access
	Service (RAS) server using 128-bit data encryption. This article describes how
	to determine whether your Windows 95-based DUN client supports this level of
	encryption.
	
	MORE INFORMATION
	================
	
	To determine if your DUN client supports 128-bit encryption, use the following
	steps:
	
	1. Click Start, point to Find, and then click Files Or Folders. In the Named
	  box, type "pppmac.vxd" (without the quotation marks), and then click Find
	  Now.
	
	2. In the list of found files, right-click the Pppmac.vxd file in the
	  Windows\System folder, and then click Properties.
	
	3. Click the Version tab.
	
	4. In the Item Name box, click Internal Name. If your computer is capable of
	  using 128-bit encryption, the text in the Value box displays:
	
	  PPPMAC (US/Canada Only, Not for Export)
	
	For additional information about 128-bit encryption, see the following articles
	in the Microsoft Knowledge Base:
	
	  Q169895 Enabling 128-bit Encryption for Routing and Remote Access
	
	
	  Q172215 How to Force 128-bit Data Encryption for RAS
	
	Additional query words: encrypt encrypted secure
	
	======================================================================
	Keywords          : kbnetwork dun win95 kbDialUp 
	Technology        : kbWin95search kbWin98search kbWin98SEsearch kbZNotKeyword3 kbWin98 kbWin98SE
	Version           : WINDOWS:; Win2000:95
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
