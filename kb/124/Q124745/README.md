---
layout: page
title: "Q124745: MHS: Incoming Messages Lose 79th Character"
permalink: /kb/124/Q124745/
---

## Q124745: MHS: Incoming Messages Lose 79th Character

{% raw %}

	Article: Q124745
	Product(s): Microsoft Mail For PC Networks
	Version(s): MS-DOS:3.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 20-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail Gateway to MHS, version 3.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Incoming messages that contain a line longer than 79 characters are wrapped
	after the 78th column, and the 79th character is deleted.
	
	CAUSE
	=====
	
	When OUTPOST.EXE parses a message, it looks for the carriage return- linefeed
	(CR/LF) combination to indicate the end of the line. The 79th character is not
	being preserved during this check.
	
	RESOLUTION
	==========
	
	A supported fix that corrects this problem is now available from Microsoft, but
	has not been fully regression-tested and should be applied only to systems
	experiencing this specific problem.
	
	To resolve this problem, contact Microsoft Product Support Services to obtain the
	fix. For a complete list of Microsoft Product Support Services phone numbers and
	information on support costs, please go to the following address on the World
	Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	The English version of this fix should have the following file attributes or
	later:
	
	  File Name     Version
	  ---------------------
	  Outpost.exe   3.0.6
	
	This hotfix has been posted to the following Internet location as Mhsgy2k.exe:
	
	  ftp://ftp.microsoft.com/bussys/mail/gateways-public/All-Y2K/
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Mail Gateway to MHS
	version 3.0.
	
	Additional query words: 3.00
	
	======================================================================
	Keywords          :  
	Technology        : kbMailSearch kbMailGateSearch kbZNotKeyword3 kbMailGateMHS300
	Version           : MS-DOS:3.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
