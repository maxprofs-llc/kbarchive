---
layout: page
title: "Q102702: Invalid VxD Dynamic Link Call to Device Number 000D"
permalink: /kb/102/Q102702/
---

## Q102702: Invalid VxD Dynamic Link Call to Device Number 000D

{% raw %}

	Article: Q102702
	Product(s): Microsoft Windows 3.x Retail Product
	Version(s): 9.0; WINDOWS:3.1,3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 06-JUN-2001
	
	3.10 3.11
	
	WINDOWS
	
	kbother kberrmsg kbinterop
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows versions 3.1, 3.11 
	- Microsoft Windows for Workgroups versions 3.1, 3.11 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you try to run Windows in 386 enhanced mode, you receive the following
	error message:
	
	  Invalid VxD dynamic link call to device number 000D, service number 000E.
	  Your Windows configuration is invalid. Run the Windows setup program again to
	  correct this problem.
	
	CAUSE
	=====
	
	Device number 000D means that the error was caused by a call to the virtual
	keyboard device referenced in the [386Enh] section of the SYSTEM.INI file. The
	default Windows entry is:
	
	       Keyboard=*vkd
	
	The Microsoft Mouse Setup version 9.0 changes this line to read:
	
	       Keyboard=C:\MOUSE\MOUSEVKD.386
	
	Third-party mouse drivers may change this line to reference a different keyboard
	driver. If Windows cannot find the driver because it has been deleted or is
	corrupted, or the keyboard= entry is missing or blank, the dynamic link call
	error message appears.
	
	RESOLUTION
	==========
	
	If you remove the Microsoft Mouse driver 9.0 and are using Microsoft Mouse
	driver 8.2, you can prevent the error message by changing the keyboard line in
	the [386Enh] section to read as follows:
	
	       Keyboard=*vkd
	
	If you are still using Microsoft Mouse driver 9.0, run Microsoft Mouse 9.0 Setup
	again to correct this error.
	
	Additional query words: 3.10 Genius serial 10.10
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbWin3xSearch kbWFWSearch kbZNotKeyword3 kbWin310 kbWin311 kbWFW310 kbWFW311
	Version           : :9.0; WINDOWS:3.1,3.11
	
	=============================================================================
	

{% endraw %}
