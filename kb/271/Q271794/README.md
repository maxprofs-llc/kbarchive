---
layout: page
title: "Q271794: Access Violation in RPCSS with Endpoint Mapper RPC Requests"
permalink: /kb/271/Q271794/
---

## Q271794: Access Violation in RPCSS with Endpoint Mapper RPC Requests

{% raw %}

	Article: Q271794
	Product(s): Microsoft Windows NT
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kbenv kberrmsg kbnetwork kbWinNT400PreSP7Fix
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Server, Enterprise Edition version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If you are running RPC-server programs that communicate with their clients over
	TCP and/or UDP and you are using dynamic endpoints while under load and
	experiencing network problems, you may receive an access violation error message
	in Rpcss.exe. When this occurs, you may need to restart the server to work
	around this problem.
	
	
	CAUSE
	=====
	
	This problem can occur because when information that is stored for datagram RPC
	requests is freed, an invalid pointer is freed that causes the access violation
	error message.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem.
	
	To resolve this problem, contact Microsoft Product Support Services to obtain the
	fix. For a complete list of Microsoft Product Support Services phone numbers and
	information on support costs, please go to the following address on the World
	Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Date        Time    Version        Size     File name    Platform
	  -----------------------------------------------------------------
	  03/21/2001  08:19p  4.0.1381.7095  602,896  Rpcrt4.dll   Alpha
	  03/21/2001  08:23p  4.0.1381.7095  343,312  Rpcrt4.dll   Intel
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT 4.0.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbenv kberrmsg kbnetwork kbWinNT400PreSP7Fix 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400 kbWinNTS400search kbWinNTS400
	Version           : :4.0
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
