---
layout: page
title: "Q197689: PRB: MSDN Causes Error After Installation on External Drives"
permalink: /kb/197/Q197689/
---

## Q197689: PRB: MSDN Causes Error After Installation on External Drives

{% raw %}

	Article: Q197689
	Product(s): Microsoft Developer Network
	Version(s): 
	Operating System(s): 
	Keyword(s): kbHTMLHelp kbGrpDSTools kbHTMLHelp121
	Last Modified: 24-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Developer Network (MSDN) 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Launching the MSDN Library and selecting the Index tab throws the following
	error:
	
	  IPF in MODULE ITSS.DLL
	
	Or a message box appears with the title:
	
	  Preparing Index For First Use ...
	
	Beneath it you will see a animation displaying a book being written using a pen
	continuously. This goes on for a long time without terminating.
	
	CAUSE
	=====
	
	This error occurs because MSDN fails to create Msdn*.chw file in the
	%WINDIR%\Help directory. By default, this is Windows\Help for Windows 95,
	Windows 98, and Windows Millennium Edition (Me) systems, and WINNT\Help for
	Windows NT 4.0 and Windows 2000. This error occurs only when installing MSDN to
	an external drive and thus the path information above is valid only for MSDN
	files installed on an external drive.
	
	NOTE: The exact name of the CHW file will change with each release of the MSDN
	Library. For example the Visual Studio 6.0 edition, the file is named
	Msdnvs98.chw. But with the April 1999 MSDN Library, the file is named
	Msdn910.chw.
	
	RESOLUTION
	==========
	
	1. Exit the MSDN Library.
	
	2. Copy the Msdn*.chw file from the MSDN directory on the first CD.
	
	3. Place the file in the %WinDir%\Help directory (see the CAUSE section in this
	  article for more details). This error occurs only when installing MSDN to an
	  external drive and thus the path information above is only valid for MSDN
	  files installed on an external drive.
	
	STATUS
	======
	
	This behavior is by design.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbHTMLHelp kbGrpDSTools kbHTMLHelp121 
	Technology        : kbHTMLHelpSearch kbAudDeveloper kbMSDNSearch kbZNotKeyword2
	Version           : :
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
