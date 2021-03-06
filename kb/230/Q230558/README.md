---
layout: page
title: "Q230558: Terminal Server Hangs and Continuously Loops in Win32k.sys"
permalink: /kb/230/Q230558/
---

## Q230558: Terminal Server Hangs and Continuously Loops in Win32k.sys

{% raw %}

	Article: Q230558
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-DEC-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Problems may occur when you run either a macro, a query on an extensive
	Microsoft Access database, or when you use either Rational or Microsoft Visual
	Test scripts. The most apparent problem is when a user session is disconnected
	when using a Rational Visual Test script against a Microsoft Excel spreadsheet,
	for example. As soon as you disconnect, Excel takes 99% of the CPU and begins to
	leak memory.
	
	This problem occurs with various server configurations including single-, dual-,
	and quad-processor systems.
	
	CAUSE
	=====
	
	This problem occurs when both Citrix ICA clients and Microsoft RDP Win32 clients
	are used. The problem seems to be far worse when using the RDP client instead of
	the ICA client. This problem also exists when you install Terminal Server
	Service Pack 4.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Windows NT Server
	4.0, Terminal Server Edition. For additional information, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q152734 How to Obtain the Latest Windows NT 4.0 Service Pack
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT Server 4.0, Terminal
	Server Edition. This problem was first corrected in Windows NT Server 4.0,
	Terminal Server Edition, Service Pack 5.
	
	MORE INFORMATION
	================
	
	Disconnected user sessions running macros cause high CPU utilization. This high
	CPU utilization could be taken by the program the macro is running against or by
	Explorer.exe. This program can not be stopped through either Task Manager or by
	using the kill command from a command prompt (Kill -f xxx or Kill xxx /id:xxx).
	In addition, the user's session cannot be reset through Tsadmin.exe. Restarting
	the server is the only way to recover. If the user reestablishes a connection,
	he/she gets a new session ID, the connection that stops responding is never
	reused. Eventually, the server running the programs does not work because of a
	lack of available resources and subsequently crashes.
	
	
	Additional query words: wts tse disconnect CPU win32k terminal server
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbNTTermServ400 kbNTTermServSearch
	Version           : winnt:4.0
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
