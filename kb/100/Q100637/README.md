---
layout: page
title: "Q100637: INFO: Specifying Icons for Console Applications in Windows NT"
permalink: /kb/100/Q100637/
---

## Q100637: INFO: Specifying Icons for Console Applications in Windows NT

{% raw %}

	Article: Q100637
	Product(s): Microsoft Programming Utilities
	Version(s): winnt:
	Operating System(s): 
	Keyword(s): 
	Last Modified: 04-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, version 1.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	In the OS/2 operating system, when you add an application to a program group and
	an icon (.ICO) file is available that has the same base name as the application,
	OS/2 displays the icon in the group file. This process does not occur
	automatically in Microsoft Windows NT; the system displays a generic icon for
	the item even when an icon with the same base name is also present.
	
	To specify the icon to appear in the program group, perform the following three
	steps:
	
	1. Create a resource (.RC) file that contains an ICON statement, such as the
	  following:
	
	        ConApp ICON ConApp.ICO
	
	2. Use the resource compiler (RC.EXE) to compile the resource file. In the
	  Visual Workbench, just add the .RC file to the list of files in the project.
	
	3. Link the compiled resource file into the application's executable file.
	
	Unlike the resource compiler provided with the 16-bit Windows development system,
	RC does not include compiled resources into the executable file or specify the
	execution environment for the application. The linker recognizes compiled
	resource files and includes them in the executable file.
	
	MORE INFORMATION
	================
	
	If you start an application by clicking its icon in Program Manager or by
	running it from the File menu in Program Manager and minimize the application,
	the system displays the icon specified in the resource file.
	
	If you start the application from the MS-DOS prompt and minimize the application,
	the system displays the icon used for the MS-DOS prompt.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbVCsearch kbAudDeveloper kbvc100
	Version           : winnt:
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
