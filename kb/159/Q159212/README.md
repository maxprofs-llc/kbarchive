---
layout: page
title: "Q159212: Office 95 Used on Windows NT or Windows 95 with Profiles"
permalink: /kb/159/Q159212/
---

## Q159212: Office 95 Used on Windows NT or Windows 95 with Profiles

{% raw %}

	Article: Q159212
	Product(s): Windows for Workgroups and Windows NT Networking Issues
	Version(s): WINDOWS:7.0,95; winnt:3.51,4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Office for Windows 95, version 7.0 
	- Microsoft Windows NT Workstation versions 3.51, 4.0 
	- Microsoft Windows NT Server versions 3.51, 4.0 
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The use of the registry for application information (instead of INI files) is
	new to Microsoft Office in version 7.0. Between user profiles and Registry
	Security under Windows NT, several issues have been encountered. The scope of
	this article is to identify and propose a resolution or workaround for each
	issue.
	
	MORE INFORMATION
	================
	
	Two Categories of Issues
	------------------------
	
	The problems occur when Office 95 is not installed under the user's login ID.
	With Windows NT 3.51, there are two primary categories of issues that will
	affect all such users; with Windows 95 with profiles, there is one. The category
	shared by both is that of missing registry entries.
	
	Missing Registry Entries
	------------------------
	
	The applications rely on information stored in Current User and Local Machine
	registry entries. Currently, Setup configures approximately 158 keys in the
	Current User section. Microsoft Word and Microsoft Excel migrate some of these
	keys, but for users who have not run Setup, about 100 keys or so will be
	missing. Most of the missing keys for Microsoft Word or Microsoft Excel are for
	more advanced functionality, but, for Microsoft PowerPoint, the loss of
	functionality is more noticeable.
	
	Solution: Setup /y /r
	
	Because more than just a few registry keys are involved, modifying the registry
	directly is not recommended. Therefore, the only solution is to have each user
	run some form of setup. When Setup is combined with specific command-line
	switches, the user is inconvenienced only once for about 3 to 5 minutes. The
	command-line switches used are /y, which specifies a setup without file copying,
	and /r, which bypasses the maintenance mode dialog box and goes directly into a
	[Reinstall]. This presents the user with no dialog boxes, but writes all the
	necessary entries into the Current User section of the registry.
	
	Because a maintenance mode [Reinstall] will be performed and will install without
	copying files, it is essential that a normal installation (including the copying
	of all necessary files) have been done on the workstation.
	
	Adding Office Setup to a Login Script
	-------------------------------------
	
	The least obtrusive way to have all users run Setup is to place it in their login
	script. In order to prevent multiple executions of Setup, you can use a
	procedure that uses two BAT files in addition to the login script modification.
	Add the following to the login script (see your network documentation for
	information on creating login scripts). This modification does not need to be,
	but can be, removed later.
	
	(The items %homeshare% and %username% are environment variables available to a
	Windows NT login script.)
	
	     REM ******** Office 95 Setup routine ********
	     IF NOT EXIST %homeshare%\%username%\OFFICE95.BAT COPY
	
	     \\<ServerA>\<ShareA>\OFFICE95.BAT %homeshare%\%username%\OFFICE95.BAT
	     %homeshare%\%username%\OFFICE95.BAT
	     REM ********
	
	This procedure copies the batch file, if it does not exist, and then runs it. The
	first time Office95.bat runs, it will start Setup with the preferred switches
	and then replace itself with a harmless, non-action batch file.
	
	     OFFICE95.BAT
	     REM ******** Office 95 Setup Batch file ********
	     \\<Server>\<Share>\<Path to Office 95>\SETUP.EXE /y /r
	     COPY \\<ServerA>\<ShareA>\POSTOFF.BAT
	     %homeshare%\%username%\OFFICE95.BAT
	     REM ********
	
	Note that the path <Server>\<Share>\<Path to Office 95> is
	replaced with the location where you installed the administration copy of Office
	95 and that <ServerA>\<ShareA> can be any common share point that
	contains these two original BAT files.
	
	     POSTOFF.BAT
	     REM ******** Post Office 95 Setup Batch file ********
	     REM    Office95 has been installed for this user
	     REM ********
	
	Caveats of Using Re-Install
	---------------------------
	
	- Users will have their own personal group under Windows NT, even if a common
	  group already exists.
	
	- Under obscure circumstances, Microsoft Word and Microsoft PowerPoint are
	  removed instead of installed. (Microsoft is still trying to isolate the
	  cause, as the problem is very difficult to reproduce.)
	
	- In a RunFromServer (RFS) installation that includes Microsoft Access, paths
	  to System.mdw and bitmaps for the Wizards are redirected to an invalid
	  location.
	
	
	Inappropriate Permission Requests of Registry Entries
	-----------------------------------------------------
	
	There are four known scenarios where Office 95 applications try to access
	information in the Registry, requesting Full Control when Read/Write is all that
	is needed. This causes the request to fail and the function may seem to not be
	installed.
	
	1. The original release of Microsoft PowerPoint requests Full Control to the
	  Shared Tools keys \\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Shared Tools and
	  all subkeys. This was corrected with Microsoft PowerPoint 7.0b, as noted in
	  Knowledge Base article Q139150, in the Microsoft PowerPoint section. A copy
	  of the maintenance release can be obtained from Microsoft Technical Support
	  or Microsoft Customer Service.
	
	2. The original release of ClipArt Gallery has the problem with
	  \\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ClipArt Gallery and all subkeys.
	
	  This problem is corrected with the updated ClipArt Gallery (Cag20a.exe). The
	  following file is available for download from the Microsoft Download Center:
	
	  Cag20a.exe
	  (http://download.microsoft.com/download/powerpoint95/Update/1/NT4/EN-US/Cag20a.exe)
	
	  Cag20a contains an updated Artgalry.exe with an accompanying ReadMe document
	  explaining the installation procedure. If a RunFromServer installation is
	  being used, a modification to the INF will also be necessary. The name of the
	  appropriate INF file will depend on the application involved but will be
	  found in the directory with Setup.exe. For example, Office 95 Professional
	  for Windows 95 will use Off95pro.inf. The following changes are necessary:
	
	  a. Make a backup copy of your INF file.
	
	  b. Open the INF using WordPad or Write.
	
	  c. Find artgalry_exe. This should bring you to the line to be modified.
	
	  d. Exit the Find dialog.
	
	  e. The version number 2.0.0.556 should be near the end of the line. Carefully
	     edit it to read 2.0.1.625, taking care not to remove any commas.
	
	3. Save the file and exit the editor.
	
	4. All versions of Microsoft Access 7.0 have the problem with
	  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Access\7.0\Wizards and all subkeys. The
	  following steps explain how to work around this issue:
	
	  a. Log on to the computer running Windows NT 3.51, as an administrator.
	
	  b. Run the Registry Editor (Regedt32.exe).
	
	  c. From the HKEY_LOCAL_MACHINE subtree, go to the following key:
	
	  SOFTWARE\Microsoft\Access\7.0\Wizards
	
	  d. On the Security menu, click Permissions.
	
	  e. Change Everyone in the permissions list from the permissions of Special
	     Access to Full Control.
	
	  f. Select the Replace Permission on Existing Subkeys check box.
	
	  g. Click OK to save the changes made to the permissions.
	
	  h. Click Yes when prompted, "Do you want to replace the permission on all
	     existing subkeys within Wizards?"
	
	  i. Exit Registry Editor.
	
	5. This last known scenario is minor in comparison to the other three. Although
	  System Info can be used from all other Office 95 applications via Help About,
	  it fails in Microsoft Excel because it tries to access the registry,
	  requesting greater permissions than needed. The affected key is
	  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Shared Tools\MSInfo. The steps to work
	  around this issue are:
	
	  a. Log on to the computer running Windows NT 3.51, as an administrator.
	
	  b. Run the Registry Editor (Regedt32.exe).
	
	  c. From the HKEY_LOCAL_MACHINE subtree, go to the following key:
	
	  SOFTWARE\Microsoft\Shared Tools\MSInfo
	
	  d. On the Security menu, click Permissions.
	
	  e. Change Everyone in the permissions list from the permissions of Special
	     Access to Full Control.
	
	  f. Click OK to save the changes made to the permissions.
	
	  g. Exit Registry Editor.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT351search kbWinNT400search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS351search kbOfficeSearch kbWin95search kbOffice95Search kbOffice95 kbZNotKeyword3 kbWin95
	Version           : WINDOWS:7.0,95; winnt:3.51,4.0
	
	=============================================================================
	

{% endraw %}
