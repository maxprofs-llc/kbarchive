---
layout: page
title: "Q309427: Err Msg Installing Reference Library: Internal Error 2894.1157"
permalink: /kb/309/Q309427/
---

## Q309427: Err Msg Installing Reference Library: Internal Error 2894.1157

{% raw %}

	Article: Q309427
	Product(s): Microsoft Home Multimedia Titles
	Version(s): 1.0
	Operating System(s): 
	Keyword(s): kberrmsg kbimu
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Encarta Reference Library 2002, version 1.0 
	- Microsoft Works Suite 2001 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you install Microsoft Encarta Reference Library 2002, you may receive the
	following error message:
	
	  Internal Error 2894.1157
	
	When you use the Microsoft Works 2001 Task Launcher, you may receive one of the
	following error messages:
	
	  The Works Task Launcher cannot access the task you selected. Necessary files
	  may be missing, corrupted, or may have been deleted. To restore or replace
	  files, reinstall Works, and then try starting the task again. If you no
	  longer use the task, with the right button, click the task name, and then
	  click Delete.
	
	  -or-
	
	  Works cannot access one or more files.
	
	  -or-
	
	  MSWORKS caused an invalid page fault in module RICHED20.DLL.
	
	CAUSE
	=====
	
	This behavior can occur if an incorrect or corrupted version of the Riched20.dll
	file is installed on your computer, or if Riched20.dll is missing.
	
	This behavior can also occur if your computer is infected with the Nimda virus
	(W32.Nimda.A@mm).
	
	If you are experiencing this behavior and you have Microsoft Office 2000
	installed, follow the steps in the following Knowledge Base article:
	
	  Q236053 OFF2000: Internal Error 2894 During Office Installation
	
	NOTE: This behavior can also occur after you have disinfected your system of the
	Nimda virus. In this case, also follow the steps in the preceding article to
	resolve the issue.
	
	
	RESOLUTION
	==========
	
	To resolve this issue, reinstall Windows Installer to repair the damaged
	Riched20.dll file. To do this, follow these steps:
	
	1. Make sure that the Nimda virus is completely removed from your system.
	
	2. Search for Riched20.dll, and then delete it if you find it.
	
	To do this, follow the steps appropriate to your operating system.
	
	Microsoft Windows 95, Microsoft Windows 98, and Microsoft Windows NT
	
	  a. Click Start, point to Find, and then click "Files or Folders".
	
	  b. In the Named box, type the following:
	
	  Riched20.dll
	
	  c. In the "Look in" box, make sure that My Computer is selected.
	
	  d. Click Find Now.
	
	  e. Delete any Riched20.dll file found in the following folders:
	
	Windows 95 and Windows 98
	
	  c:\Windows\System
	
	Windows NT
	
	  c:\Windows\System32
	
	  f. Close the Search Results dialog box.
	
	Microsoft Windows Millennium Edition (Me) and Microsoft Windows 2000
	
	  a. Click Start, point to Search, and then click "For Files or Folders".
	
	  b. In the "Search for files or folders named" box, type the following:
	
	  Riched20.dll
	
	  c. In the "Look in" box, make sure that My Computer is selected.
	
	  d. Click Search Now.
	
	  e. Delete any Riched20.dll file found in the following folders:
	
	Windows Me
	
	  c:\Windows\System
	
	Windows 2000
	
	  c:\Windows\System32
	
	  f. Close the Search Results dialog box.
	
	3. Install Windows Installer.
	
	  To do this, use one of the following methods.
	
	METHOD 1
	
	Download the latest version of Windows Installer from the Microsoft Download
	Center. To do this, browse to the link appropriate to your version of Windows.
	
	  Windows 95, Windows 98, and Windows Me
	
	  http://www.microsoft.com/downloads/release.asp?ReleaseID=32831
	  (http://www.microsoft.com/downloads/release.asp?ReleaseID=32831)
	
	  Windows NT and Windows 2000
	
	  http://www.microsoft.com/downloads/release.asp?ReleaseID=32832
	  (http://www.microsoft.com/downloads/release.asp?ReleaseID=32832)
	
	METHOD 2
	
	Install the original version of Windows Installer from the Microsoft Windows
	CD-ROM.
	
	On a Windows 95, Windows 98, or Windows Me-based computer, open the Msi folder on
	the Windows CD-ROM, and then double-click Instmsi.exe.
	
	-or-
	
	On a Windows NT 4.0 or Windows 2000-based computer, open the Msi folder on the
	Windows CD-ROM, and then double-click Instmsiw.exe.
	
	METHOD 3
	
	If you do not have the Windows CD-ROM, you may find the Windows Installer files
	on the CD-ROM for each individual program. Follow the steps appropriate to the
	program.
	
	Microsoft Encarta Reference Library 2002
	
	  1. Insert the Installation & Resources CD-ROM into your computer's CD-ROM
	     or DVD-ROM drive.
	
	  2. Click Start, and then click Run.
	
	  3. On a Windows 98 or Windows Me-based computer, type the following in the
	     Open box
	
	  <d>:\instmisa.exe
	
	where <d> is the drive letter of your computer's CD-ROM or DVD-ROM drive.
	
	  4. On a Windows NT or Windows 2000-based computer, type the following in the
	     Open box
	
	  <d>:\instmisw.exe
	
	where <d> is the letter of your CD-ROM or DVD-ROM drive.
	
	  5. Follow the instructions for installation.
	
	Microsoft Works Suite 2001
	
	  1. Insert Disk 1 into your computer's CD-ROM or DVD-ROM drive.
	
	  2. Click Start, and then click Run.
	
	  3. On a Windows 98 or Windows Me-based computer, type the following in the
	     Open box
	
	  <d>:\MSWorks\instmisa.exe
	
	where <d> is the letter of your CD-ROM or DVD-ROM drive.
	
	  4. On a Windows NT or Windows 2000-based computer, type the following in the
	     Open box
	
	  <d>:\MSWorks\instmisw.exe
	
	where <d> is the letter of your CD-ROM drive.
	
	  5. Follow the instructions for installation.
	
	MORE INFORMATION
	================
	
	For additional information, click the article number below to view the article
	in the Microsoft Knowledge Base:
	
	  Q308225 Error Message: Windows Installer Internal Error 2889_ISAPATHDLG
	
	Additional query words:
	
	======================================================================
	Keywords          : kberrmsg kbimu 
	Technology        : kbHomeProdSearch kbWorksSearch _IKkbbogus kbEncartaSearch kbMMSearch kbEncartaRef2002
	Version           : :1.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
