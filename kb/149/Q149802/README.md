---
layout: page
title: "Q149802: Assigning 3270 LUs to Workstations Using SNA Server Client"
permalink: /kb/149/Q149802/
---

## Q149802: Assigning 3270 LUs to Workstations Using SNA Server Client

{% raw %}

	Article: Q149802
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:2.0,2.1,2.11,2.11 SP1
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 2.0, 2.1, 2.11, 2.11 SP1, on platform(s):
	   - the operating system: Microsoft Windows NT 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	SNA Server does not provide a direct way of assigning LUs to a specific
	workstation using the SNA Server Admin program. The only way to assign LUs to a
	workstation is by setting the LocalLUs parameter.
	
	MORE INFORMATION
	================
	
	SNA Server version 2.x does not provide a centralized method of assigning LUs to
	workstations. The SNA Server Admin does allow the assignment of LUs to a
	particular user or group. The local LU feature implemented in SNA Server client
	software can be used to limit which LUs can be used on the client computer, and
	it can be used to implement LU assignment to a workstation.
	
	The following procedure can be implemented on an MS-DOS, Microsoft Windows 3.x,
	Microsoft Windows NT, and Microsoft Windows 95 client.
	
	NOTE: The steps that are platform dependent will identify the procedure to follow
	for each component.
	
	1. Determine what LUs will belong to which workstations, and what users will be
	  using each workstation.
	
	2. Using SNA Admin, assign specific LUs to the users or groups that they will be
	  accessing from these workstations. The assignment of LU pools is not
	  supported when you implement this specific procedure.
	
	3. In the SNA client configuration, specify the specific LUs that the
	  workstation will be limited to, using the LocalLU parameter:
	
	MS-DOS clients
	--------------
	
	- Open the Sna.ini file on each MS-DOS workstation using Edit.com or similar
	  text editor.
	
	- Add the following entry in the [SnaBase] section of the Sna.ini file:
	
	          LocalLUS=<LocalLUName1> <LocalLUName2> ... <LocalLUNamex>
	
	  where <LocalLUNamex> are LU names separated by spaces.
	
	- Close and save the Sna.ini file.
	
	Windows 3.X/Windows for Workgroups clients
	------------------------------------------
	
	- Make a backup of the Win.ini file. Open the Win.ini file from the Windows
	  root directory using Notepad.
	
	- Add the following entry in the [Wnap] section of Win.ini:
	
	          LocalLUS=<LocalLUName1> <LocalLUName2> ... <LocalLUNamex>
	
	  where <LocalLUNamex> are LU names separated by spaces.
	
	- Close and save the Win.ini file.
	
	Windows NT clients
	------------------
	
	WARNING: Using Registry Editor incorrectly can cause serious, system- wide
	problems that may require you to reinstall Windows NT to correct them. Microsoft
	cannot guarantee that any problems resulting from the use of Registry Editor can
	be solved. Use this tool at your own risk.
	
	- Run the Registry Editor (Regedt32), and locate the following key:
	
	       HKEY_LOCAL_MACHINE
	           SYSTEM
	                CurrentControlSet
	                    Services
	                        SnaBase
	                            Parameters
	
	- Add the following value to the Registry key:
	
	       Value Name: LocalLUS
	        Data Type: REG_MULTI_SZ
	             Data: <LocalLUName1> <LocalLUName2> ... <LocalLUNamex>
	
	  where <LocalLUNamex> are LU names separated by spaces.
	
	- Close the Registry Editor.
	
	Windows 95 clients
	------------------
	
	WARNING: Using Registry Editor incorrectly can cause serious, system- wide
	problems that may require you to reinstall Windows NT to correct them. Microsoft
	cannot guarantee that any problems resulting from the use of Registry Editor can
	be solved. Use this tool at your own risk.
	
	- Run the Registry Editor (REGEDIT), and locate the following key:
	
	        HKEY_LOCAL_MACHINE
	            SOFTWARE
	                Microsoft
	                    SnaBase
	                         Parameters
	
	- Add the following string value to the Registry key:
	
	       String Value Name: LocalLUS
	                    Data: <LocalLUName1> <LocalLUName2> ...<LocalLUNamex>
	
	  where <LocalLUNamex> are LU names separated by spaces.
	
	- Close the Registry Editor.
	
	After you follow these steps, run the 3270 application. The list of available LUs
	for that workstation should match those entered in the LocalLUS parameter. If
	you do not have access to the LU chosen, the emulator should report an error. To
	correct this problem, add the LU to the user (or group) record in SNA Admin.
	
	This procedure should affect all emulators that use the SNA Server client.
	
	The problems of assigning LUs to workstations with this method are the
	following:
	
	- Station is limited to the LUs listed; no matter what user is signed on.
	
	- Security for a broad range of LUs must be assigned to all users.
	
	- The administrator is responsible for securing the Win.ini file (Windows 3.x),
	  SNA.INI (MS-DOS), or the Registry (Windows 95, Windows NT) against users
	  wishing to broaden their LU selection.
	
	NOTE: There is currently a problem assigning Printer LUs. At present, Printer LUs
	are mapped to Display LUs by mistake.
	
	
	Additional query words: prodsna
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbAudDeveloper kbSNAServSearch
	Version           : WINDOWS:2.0,2.1,2.11,2.11 SP1
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
