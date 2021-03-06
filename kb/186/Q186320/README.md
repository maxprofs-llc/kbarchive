---
layout: page
title: "Q186320: INFO: Determining if a Web Project is Source Code Controlled"
permalink: /kb/186/Q186320/
---

## Q186320: INFO: Determining if a Web Project is Source Code Controlled

{% raw %}

	Article: Q186320
	Product(s): Microsoft SourceSafe
	Version(s): WINDOWS:1.0,5.0,97
	Operating System(s): 
	Keyword(s): 
	Last Modified: 01-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual SourceSafe for Windows, version 5.0 
	- Microsoft FrontPage 97 for Windows 
	- Microsoft Visual InterDev, version 1.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When developing a Web with either FrontPage or Visual Interdev, you may want to
	know the following:
	
	- If SourceSafe integration is available.
	
	- Whether a specific Web is source controlled and the name of the controlling
	  project.
	
	- Find which VSS database the Web is connected to.
	
	MORE INFORMATION
	================
	
	Determining if SourceSafe Integration is Available
	--------------------------------------------------
	
	  FrontPage: From the Tools menu choose Web settings. If there is no Source
	  Control Project field, source control is unavailable.
	
	  Visual Interdev: From the Project Menu, choose Enable Web Source Control, and
	  then enter a project name in the "Enable Source Control" dialog box. The
	  operation fails and returns an error message if source control is
	  unavailable.
	
	Determining if a Web is Source Controlled
	-----------------------------------------
	
	  FrontPage: From the View menu choose Folder View. Files that are Source
	  controlled have an additional glyph to the left of the file name. A green dot
	  for a checked in file, a red check mark for a file checked out to the current
	  user, or a padlock if the file is checked out to a different user. The
	  controlling project name displays in the Source Control Project field on the
	  Configuration tab of the Tools ... Web settings dialog box. If this field is
	  empty, source control is not enabled for this Web.
	
	  Interdev: Right-click the Web name in the File View pane and choose
	  Properties from the shortcut menu. The Web Server tab of the Properties
	  dialog box either displays the controlling project name, or indicates that
	  the Web does not have source control enabled.
	
	Finding Which VSS Database the Web is Connected to
	--------------------------------------------------
	
	  The Service.cnf file, located in the Inetpub\wwwroot\webname\_vti_pvt folder
	  has the following line for a Source Code controlled Web:
	  vti_sourcecontrolcookie equals the path to Srcsafe.ini
	
	REFERENCES
	==========
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q171116 HOWTO: Enable VSS Integration with FrontPage and Visual Interdev
	
	(c) Microsoft Corporation 1998, All Rights Reserved. Contributions by David de
	Groot, Microsoft Corporation
	
	
	Additional query words: ssfp ssidev kbDSupport kbdse
	
	======================================================================
	Keywords          :  
	Technology        : kbVisIDsearch kbSSafeSearch kbFrontPageSearch kbAudDeveloper kbFrontPage97 kbZNotKeyword2 kbFrontPage97Search kbVisID100 kbSSafe500
	Version           : WINDOWS:1.0,5.0,97
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
