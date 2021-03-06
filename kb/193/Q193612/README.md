---
layout: page
title: "Q193612: Log Files Rolled Over According to GMT, Not Local Time Zone"
permalink: /kb/193/Q193612/
---

## Q193612: Log Files Rolled Over According to GMT, Not Local Time Zone

{% raw %}

	Article: Q193612
	Product(s): Internet Information Server
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kbFEA kbWinNT400sp4fea kbWinNT4sp6fix
	Last Modified: 16-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	- Microsoft Internet Information Server version 4.0 
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Log files roll over at midnight Greenwich Mean Time (GMT) rather than at
	midnight according to the local time zone.
	
	CAUSE
	=====
	
	Microsoft Internet Information Server follows the World Wide Web Consortium
	(W3C) specification of rolling over the log at midnight GMT.
	
	RESOLUTION
	==========
	
	Windows NT Server or Workstation 4.0
	------------------------------------
	
	To resolve this problem, obtain the latest service pack for Windows NT 4.0 or the
	individual software update. For information on obtaining the latest service
	pack, please go to:
	
	- http://www.microsoft.com/Windows/ServicePacks/
	
	-or-
	
	- Q152734 How to Obtain the Latest Windows NT 4.0 Service Pack
	
	For information on obtaining the individual software update, contact Microsoft
	Product Support Services. For a complete list of Microsoft Product Support
	Services phone numbers and information on support costs, please go to the
	following address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	
	Windows NT Server 4.0, Terminal Server Edition
	----------------------------------------------
	
	To resolve this problem, obtain the latest service pack for Windows NT Server
	4.0, Terminal Server Edition. For additional information, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q152734 How to Obtain the Latest Windows NT 4.0 Service Pack
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article. This problem was first corrected in
	Windows NT Server version 4.0, Terminal Server Edition Service Pack 6.
	
	MORE INFORMATION
	================
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q194699 Extended Log File Format Always in GMT
	
	In Service Pack 4, the behavior was changed so that Log files roll over at
	midnight according to the local time zone when metabase property ID 4015 is set
	to 1 using MetaEdit (shipped with the IIS Resource Kit) for each concerned Web
	site.
	
	You can use the following command to add this metabase key:
	
	  mdutil.exe SET -svc w3svc -i 1 -utype UT_SERVER -dtype DWORD -attrib INHERIT
	  -prop 4015 -value 1
	
	Where -svc is the name of the service (for FTP, the service would be MSFTPSVC)
	and -i is set to the number of the Web site where you want to set the logging
	parameter.
	
	
	Additional query words: rolled over new daily day mid-night midnite mid-nite 12am 12:00 a.m. akz
	
	======================================================================
	Keywords          : kbFEA kbWinNT400sp4fea kbWinNT4sp6fix 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbNTTermServ400 kbNTTermServSearch kbiisSearch kbiis400
	Version           : :4.0
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
