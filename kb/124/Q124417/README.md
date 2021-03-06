---
layout: page
title: "Q124417: Display Problems or Computer Hangs When You Play Video Clips"
permalink: /kb/124/Q124417/
---

## Q124417: Display Problems or Computer Hangs When You Play Video Clips

{% raw %}

	Article: Q124417
	Product(s): Microsoft Home Multimedia Titles
	Version(s): 1.0,1995 edition,3.11
	Operating System(s): 
	Keyword(s): kbmm kbprbkbfaq
	Last Modified: 09-NOV-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Ancient Lands for Windows, version 1.0 
	- Microsoft Bookshelf '95 for Windows 95 
	- Microsoft Bookshelf 1996-97 for Windows 
	- Microsoft Cinemania 1995 edition 
	- Microsoft Complete Baseball for Windows, 1994 edition (see below) 
	- Microsoft Dangerous Creatures for Windows, version 1.0 
	- Microsoft Dinosaurs for Windows, version 1.0 
	- Microsoft Encarta 96 Encyclopedia for Windows 
	- Microsoft Encarta 1994 The Complete Multimedia Encyclopedia 
	- Microsoft Encarta 97 Encyclopedia for Windows 
	- Microsoft Julia Child: Home Cooking with Master Chefs for Windows, version 1.0 
	- Scholastic's Magic School Bus series: Explores Inside the Earth for Windows, version 1.0 
	- Scholastic's Magic School Bus series: Explores the Human Body for Windows, version 1.0 
	- Scholastic's Magic School Bus series: Explores the Ocean for Windows, version 1.0 
	- Scholastic's Magic School Bus series: Explores the Solar System for Windows, version 1.0 
	- the operating system: Microsoft Windows 3.11 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you play a video clip, you may experience any of the following symptoms:
	
	- The system may hang (stop responding).
	- The video may flash.
	- Distortion is observed in the video playback area.
	- The video may just show a blank window, a white window, or a black window,
	  even though the sound plays correctly.
	- Some computers may experience hesitation problems with the video, where it
	  continually starts and stops instead of playing smoothly.
	- Videos only play in the large or expanded mode. The normal mode videos do not
	  play.
	
	This problem has been reported on the following systems:
	
	- Compaq Prolinea and Compaq Presario computers using the Compaq/ET4000-W32 640
	  x 480 256-color display driver
	- Cardinal VGA 732 with the TSENG ET Turbo 4000 driver
	- Cardinal with Tseng Laboratories 988/ET4 Turbo driver
	- Diamond Stealth 64 video driver
	- IBM ThinkPad
	- Diamond Speedstar 64 (non-PCI)
	- Orchid Kelvin 64 w/ version 1.4 driver
	- STB Vision Meta driver
	- Gateway P5-100 with STB Vision Display Meta Driver
	- STB PowerGraph VLB 24 video adapter
	- STB Vision Meta Driver
	
	
	RESOLUTION
	==========
	
	To solve this problem, add the following line to the [drawdib] section of the
	Win.ini file:
	
	  dva=0
	
	
	MORE INFORMATION
	================
	
	The "dva=0" entry turns off direct video access (DVA) and DCI, components of
	Microsoft Video For Windows. DVA and DCI allow video images to be sent directly
	to the screen. If an application detects the display type incorrectly, problems
	can occur using DVA and DCI. Some of these problems can be severe (such as
	general protection (GP) faults in Gdi.exe). When you turn off DVA and DCI, video
	images must be drawn through GDI. Although using GDI can be slower than direct
	access, it is safer. This problem does not occur when using Microsoft Video for
	Windows version 1.1d or later.
	
	
	The third-party products discussed in this article are manufactured by vendors
	independent of Microsoft; we make no warranty, implied or otherwise, regarding
	these products' performance or reliability.
	
	Additional query words: multi-mediamm movie corruption distorted distortion jump blink avi vfw msbsolar msb-ss schoolbus mskids magic errors gpf blank black
	
	======================================================================
	Keywords          : kbmm kbprb kbfaq
	Technology        : kbOSWinSearch kbHomeProdSearch kbHomeMMsearch kbZNotKeyword6 kbEncartaSearch kbGamesSearch kbZNotKeyword kbKidsSearch kbBookshelfSearch kbBaseballSearch kbEncartaEncycSearch kbCineManiaSearch kbAncientLands kbBookShelf1995 kbBookShelf1996 kbBookShelf1997 kbCinemania1995 kbCompleteBaseball1994 kbDangerousCreatures kbDinosaurs100 kbJuliaChild kbScholasticHuman kbScholasticOcean kbScholasticSolar kbScholasticEarth kbEncartaEnCyc1996 kbEncartaEnCyc1997 kbEncartaEnCyc1994 kbOSWin311 kbMSBSearch
	Version           : :1.0,1995 edition,3.11
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
