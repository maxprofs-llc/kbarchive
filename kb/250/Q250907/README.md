---
layout: page
title: "Q250907: XFOR: Cannot Open Internet Mail Service Page with SMTP Error"
permalink: /kb/250/Q250907/
---

## Q250907: XFOR: Cannot Open Internet Mail Service Page with SMTP Error

{% raw %}

	Article: Q250907
	Product(s): Microsoft Exchange
	Version(s): 5.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 23-OCT-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you delete the Extension for Internet Mail Service For i386 from the
	Add-Ins container in the Exchange Administrator program, and then attempt to
	open the Internet Mail Service properties page, you may receive the following
	message:
	
	  Extension SMTP could not be loaded.
	  The extension for Microsoft Exchange Administrator's CPU type has not been
	  installed in the site.
	  Microsoft Exchange Administrator
	  ID no: c1031667
	
	CAUSE
	=====
	
	This behavior can occur when the Exchange Administrator program cannot load the
	Imcadmin.dll file because the extension object is missing or has been deleted
	from the Exchange Administrator directory.
	
	RESOLUTION
	==========
	
	CAUTION: Using the raw mode of the Exchange Administrator program (admin /r)
	incorrectly can cause serious problems that may require you to reinstall
	Microsoft Windows NT Server, Microsoft Exchange Server, or both. Microsoft
	cannot guarantee that problems resulting from the incorrect use of raw mode can
	be solved. Use raw mode at your own risk.
	
	NOTE: If you click Ignore instead of Abort or Retry in the error message box, the
	Internet Mail Service properties page opens.
	
	To resolve this behavior, re-create the directory extension object in raw mode of
	the Exchange Administrator program. Follow these steps:
	
	1. Run Windows Explorer to confirm that X:\Exchsrvr\Add-Ins contains the
	  Imcadmin.dll file. If the file is missing, you can replace it from the
	  Setup\I386 or Alpha\Add- ins\Smtp\I386 or Alpha directory on the Microsoft
	  Exchange Server CD.
	
	  NOTE: If this file exists on another Exchange Server computer on the same
	  site, it is dynamically replicated when the Internet Mail Service property
	  page is opened.
	
	2. Log on to Exchange Server with the Exchange Server Service account.
	
	3. At the command prompt, use the cd command to change to the Exchsrvr/Bin
	  directory.
	
	4. Use the admin /r command, and then press ENTER. This opens the Exchange
	  Administrator program in raw mode.
	
	5. On the site level, expand the Configuration container, and then click the
	  Add-Ins container.
	
	6. From the File menu, click New Other, and then click Raw Object.
	
	7. In the New Raw Object dialog box, click Admin-Extension, and then click OK.
	
	8. In the Properties page, click Directory Name, and under Edit Value, type
	  "SMTP:i386" (without the quotation marks) and then click Set.
	
	9. Click File-Version, and under Edit Value, type the hexadecimal value for the
	  version and then click Set.
	
	  NOTE: You can find the hexadecimal number by looking at the same directory
	  object on another Exchange Server 5.5 computer that is running the same
	  service pack. This value can be found in the site level, expand the
	  Configuration container, and then click the Add-Ins container. Select the Raw
	  Properties of "Extensions for Internet Mail Service for I386". Then choose
	  the File-Version object.
	
	10. Click Admin-Extension-Dll, and under Edit Value, type "Imcadmin.dll"
	  (without the quotation marks), and then click Set.
	
	11. Click OK.
	
	12. Expand the Add-Ins container, open the SMTP:i386 Properties page, and in the
	  Display Name box, type "Extension for Internet Mail Service for i386"
	  (without the quotation marks), and then click OK.
	
	13. Expand the Connections container, and then attempt to open the Internet Mail
	  Service Properties page. If you cannot access the Internet Mail Service
	  Properties page, delete and then re-create the extension object.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : :5.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
