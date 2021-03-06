---
layout: page
title: "Q92901: Mouse Problems with Swap File and LRU Settings"
permalink: /kb/092/Q92901/
---

## Q92901: Mouse Problems with Swap File and LRU Settings

{% raw %}

	Article: Q92901
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:3.1,3.11
	Operating System(s): 
	Keyword(s): win31
	Last Modified: 26-SEP-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows versions 3.1, 3.11 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article discusses using least recently used (LRU) paging settings in the
	[386enh] section of the SYSTEM.INI as a possible solution to erratic mouse
	behavior when a swap file is active.
	
	You should use these steps only after you have determined that a mouse problem is
	present only when Windows 3.1 is configured to use virtual memory.
	
	MORE INFORMATION
	================
	
	If you experience missed mouse clicks or jerky mouse movements in Windows while
	a swap file is active, you may need to adjust the frequency of the LRU rate in
	Windows.
	
	Missed mouse clicks are mouse button actions that seem to be ignored by Windows.
	A "stuck" mouse button or click refers to a situation in which Windows seems to
	lock the mouse button down. This locking causes a "runaway" effect when
	scrolling. Scrolling will seem automatic for up to a few seconds.
	
	The LRU settings are outlined on pages 205-206 of the Windows Resource Kit for
	Windows 3.1 and, in general, these settings should not be changed. To determine
	if your mouse problem is related to the swap file LRU settings, place the
	following line in the [386enh] section of your SYSTEM.INI:
	
	  paging=off
	
	If this setting does not improve Windows mouse movement, then general mouse
	troubleshooting should be performed. The LRU settings should not be changed.
	
	Microsoft has an article available that outlines general mouse troubleshooting.
	The article "Troubleshooting Microsoft and Compatible Mice in Windows" (Q88543)
	can be obtained by contacting Microsoft Product Support Services.
	
	If testing with "paging=off" resolves the erratic mouse symptoms, remove the
	"paging=off" statement from the SYSTEM.INI file and add the following lines to
	the [386enh] section of the SYSTEM.INI:
	
	  LRULowRateMult=1
	
	This sets the low LRU rate = to the high LRU rate.
	
	  LRUSweepFreq=x
	
	This sets the high LRU rate, the default is 250 (1/4 of a second):
	
	  x=60000 = 1 Minute
	  x=600000 = 10 Minutes
	  x=6000000 = 1,000 Minutes (about 16 hours)
	  x=60000000 = 10,000 Minutes (about 6 days)
	  x=600000000 = 100,000 Minutes (about 60 days)
	
	Try 60000 first; if that behaves, try 600000000.
	
	NOTE: You may need to experiment some to determine the proper LRU settings.
	
	These settings adjust how Windows uses virtual memory. Different settings for
	LRUSweepFreq may be needed depending on if a temporary or permanent swap file is
	used.
	
	For more information about erratic mouse behavior, see the "Mouse Pointer
	Movement Is Erratic" section in the following article in the Microsoft Knowledge
	Base.
	
	  Q88543 Troubleshooting Microsoft and Compatible Mice in Windows
	
	
	Additional query words: 3.10 jumpy
	
	======================================================================
	Keywords          : win31 
	Technology        : kbWin3xSearch kbZNotKeyword3 kbWin310 kbWin311
	Version           : WINDOWS:3.1,3.11
	
	=============================================================================
	

{% endraw %}
