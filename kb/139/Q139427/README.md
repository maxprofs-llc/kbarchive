---
layout: page
title: "Q139427: Using Long Filenames with the Run Command"
permalink: /kb/139/Q139427/
---

## Q139427: Using Long Filenames with the Run Command

{% raw %}

	Article: Q139427
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): 95 4.00
	Operating System(s): 
	Keyword(s): win95
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If you click Run on the Start menu and then type a command including a long
	filename with an embedded space in the Run dialog box, one of the following
	symptoms may occur:
	
	- You receive the following error message: Cannot find <filename> (or one
	  of its components). Make sure the path and filename are correct and that all
	  required libraries are available.
	
	- An incorrect folder is opened or the wrong file is run.
	
	CAUSE
	=====
	
	Commands containing long filenames with embedded space characters must be
	enclosed in quotation marks in the Run dialog box.
	
	Note that long filenames that do not contain embedded spaces are processed
	correctly.
	
	RESOLUTION
	==========
	
	To resolve this issue, use either of the following methods:
	
	- To use a command including a long filename with an embedded space character
	  in the Run dialog box, you must enclose the entire command in quotation
	  marks. For example, to run the command
	
	  c:\program files\accessories\mspaint.exe
	
	  you must type the following line in the Run dialog box (including the
	  quotation marks:
	
	  "c:\program files\accessories\mspaint.exe"
	
	- In the Run dialog box, use the 8.3 alias for any folder or filename that
	  contains embedded spaces. For example, instead of typing
	
	  "c:\program files\accessories\mspaint.exe"
	
	  in the Run dialog box, you could type:
	
	  c:\progra~1\accessories\mspaint.exe
	
	  In this example, "progra~1" is the 8.3 alias for the long filename "program
	  files."
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	When you type a long filename with embedded spaces without quotation marks in
	the Run dialog box, the filename is truncated at the first space when the
	command is processed.
	
	Additional query words: 4.0 LFN
	
	======================================================================
	Keywords          : win95 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWin95search kbZNotKeyword3
	Version           : 95 4.00
	
	=============================================================================
	

{% endraw %}
