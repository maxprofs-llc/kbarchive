---
layout: page
title: "Q93164: WFWG: Network Button Does Not Appear in Open Dialog Box"
permalink: /kb/093/Q93164/
---

## Q93164: WFWG: Network Button Does Not Appear in Open Dialog Box

{% raw %}

	Article: Q93164
	Product(s): Microsoft Windows 3.x Retail Product
	Version(s): WINDOWS:3.1,3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 07-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows for Workgroups versions 3.1, 3.11 
	- Microsoft Windows 3.11 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When you are running Windows for Workgroups 3.1 or 3.11 or Windows 3.11, a
	button labeled "Network" usually appears in the Open common dialog box. If the
	Network button doesn't appear in the Open dialog box of a specific application,
	one of the following conditions exists:
	
	- The application does not support common dialog boxes.
	
	- The application does not have enough stack space left.
	
	- The common dialog template of the application doesn't have enough room to
	  display the Network button.
	
	- Windows is finding an older COMMDLG.DLL in the search path that doesn't have
	  the Network button option.
	
	- There is a control ID conflict. (The ID is psh14.)
	
	MORE INFORMATION
	================
	
	The Application Does Not Support Common Dialog Boxes
	----------------------------------------------------
	
	An application must be written to use the Common Dialog Boxes dynamic link
	library (COMMDLG.DLL). If it was not, the Network button does not appear in the
	dialog box.
	
	To determine if an application uses common dialog boxes, rename COMMDLG.DLL to
	COMMDLG.OLD, and then run the application. If the application uses COMMDLG.DLL,
	you receive the following error message:
	
	  Cannot find COMMDLG.DLL
	
	The Application Does Not Have Enough Stack Space Left
	-----------------------------------------------------
	
	An application must have approximately 7 kilobytes (K) of stack space to display
	the Network button in the Open dialog box. The amount of free stack space is
	application dependent and cannot be altered by Windows.
	
	The Applications Common Dialog Template Doesn't Have Enough Room
	----------------------------------------------------------------
	
	Applications use a template when a common dialog box is called. After the
	application has added its buttons, Windows adds buttons to space that remains.
	If there is not enough room below the OK button, the Network button is not
	added. Use of the common dialog template is application dependent and cannot be
	altered by Windows.
	
	
	Windows Is Finding an Older COMMDLG.DLL in the Search Path That Doesn't
	Have the Network Button Option
	------------------------------------------------------------------------------------------------------
	
	To correct this problem, rename the COMMDLG.DLL in the application's directory
	and copy the Windows for Workgroups or Windows 3.11 version of the file to the
	application's directory.
	
	There Is a Control ID Conflict. (The ID Is psh14.)
	--------------------------------------------------
	
	If there is a control ID conflict, the Network button does not appear in the Open
	dialog box. For more information, contact the manufacturer of the application
	with which you are having problems.
	
	Additional query words: 3.10 3.11 Novell Update
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbWin3xSearch kbWFWSearch kbZNotKeyword3 kbWin311 kbWFW310 kbWFW311
	Version           : WINDOWS:3.1,3.11
	
	=============================================================================
	

{% endraw %}
