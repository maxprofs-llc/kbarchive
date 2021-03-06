---
layout: page
title: "Q249245: IIS Global - Objects Counter Never Decreases"
permalink: /kb/249/Q249245/
---

## Q249245: IIS Global - Objects Counter Never Decreases

{% raw %}

	Article: Q249245
	Product(s): Internet Information Server
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kbWinNT400PreSP7Fix
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Server version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you use Performance Monitor (Perfmon) to monitor Internet Information
	Server (IIS), the Internet Information Services - objects counter increases
	unexpectedly. This occurs only when all of the following conditions are met:
	
	- Your are using Windows NT Challenge/Response to secure the Web site.
	
	- Default document mapping is used.
	
	Note that the counter never decreases until you stop the Iisadmin service.
	
	WORKAROUND
	==========
	
	To work around this issue, do one of the following:
	
	- Secure all documents except the default document.
	
	-or-
	
	- Do not use default document mapping.
	
	The counter will then behave as expected.
	
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
	
	  Date      Time    Version      Size    File name     Platform
	  -------------------------------------------------------------
	  01/21/00  22:20   4.02.0738    185.760 Infocomm.dll  x86
	  01/21/00  22:20   4.02.0738    228.480 W3svc.dll     x86
	
	  01/21/00  22:20   4.02.0738    304.400 Infocomm.dll  alpha
	  01/21/00  22:21   4.02.0738    383.760 W3svc.dll     alpha
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Internet Information Server 4.0.
	
	MORE INFORMATION
	================
	
	If the home directory of a Web site and the default document are secured with
	Windows NT Challenge/Response, and the default document is implicitly loaded
	(without the default document name specified in the URL), the Internet
	Information Services - objects counter increases by one for requests to the
	default document. The counter never decreases.
	
	This is not a memory leak, but a problem setting the counter to the correct
	value.
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbWinNT400PreSP7Fix 
	Technology        : kbiisSearch kbiis400
	Version           : winnt:4.0
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
