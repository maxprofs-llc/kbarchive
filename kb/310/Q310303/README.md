---
layout: page
title: "Q310303: PRB: Package and Deployment Wizard Does Not Distribute MDAC 2.6"
permalink: /kb/310/Q310303/
---

## Q310303: PRB: Package and Deployment Wizard Does Not Distribute MDAC 2.6

{% raw %}

	Article: Q310303
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 2.1,2.5,2.6,2.7,6.0
	Operating System(s): 
	Keyword(s): kbwizard kbAppSetup kbDeployment
	Last Modified: 31-JAN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	- Microsoft Data Access Components versions 2.1, 2.5, 2.6, 2.7 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When your Visual Basic project references the Microsoft ActiveX Data Objects
	library, if you use the Package and Deployment Wizard (PDW) to build the
	installation package, the Package and Deployment Wizard includes the
	Mdac_typ.exe file to install Microsoft Data Access Components (MDAC) on the
	target computer. The Mdac_typ.exe is located in the following folder:
	
	  \Program Files\Microsoft Visual Studio\VB98\Wizards\PDWizard\Redist
	
	However, every time you update MDAC, you do not guarantee that the Mdac_typ.exe
	file is also updated.
	
	RESOLUTION
	==========
	
	To distribute the correct Mdac_typ.exe file with your application, you must
	replace the version of Mdac_typ.exe in the \Program Files\Microsoft Visual
	Studio\VB98\Wizards\PDWizard\Redist folder with the correct version of that
	file.
	
	MORE INFORMATION
	================
	
	You can use several methods to update MDAC on the development system. For
	example, you can use Visual Basic service packs or Microsoft SQL Server updates
	to update your version of MDAC. You can also download the latest version of the
	MDAC from the Web. However, none of these methods guarantee that the
	Mdac_typ.exe file is also updated.
	
	When you install a Visual Basic service pack, the service pack may or may not
	update MDAC and the Mdac_typ.exe file. The following table outlines the behavior
	of the last three Visual Basic 6.0 service packs:
	
	+------------------------------------------------------------------------------------------------------------+
	| Visual Basic 6.0 Service Pack | Includes MDAC Upgrade | Installs MDAC Automatically | Updates Mdac_typ.exe | 
	+------------------------------------------------------------------------------------------------------------+
	| Service Pack 3                | Yes (MDAC 2.1)        | Yes                         | Yes (2.1.1.3711.11)  | 
	+------------------------------------------------------------------------------------------------------------+
	| Service Pack 4                | Yes (MDAC 2.5)        | No                          | Yes (2.50.4403.12)   | 
	+------------------------------------------------------------------------------------------------------------+
	| Service Pack 5                | Yes (MDAC 2.6)        | No                          | No                   | 
	+------------------------------------------------------------------------------------------------------------+
	
	If you use any method other than a Visual Basic service pack to update MDAC, the
	Mdac_typ.exe file is not updated automatically. You must manually copy the
	Mdac_typ.exe file in the above-mentioned folder for the version of MDAC that is
	installed.
	
	To determine the version number of a file, follow these steps:
	
	1. Open Microsoft Explorer.
	
	2. Browse to the following folder:
	
	  \Program Files\Microsoft Visual Studio\VB98\Wizards\PDWizard\Redist
	
	3. Right-click Mdac_typ.exe, and then click Properties.
	
	4. Click the Version tab. The file version appears at the top of this tab.
	
	The following table lists the file versions for the Mdac_typ.exe file and its
	associated MDAC version.
	
	  
	  +------------------------------------------+
	  | MDAC Version | Mdac_typ.exe File Version | 
	  +------------------------------------------+
	  | MDAC 2.0     | 4.71.1015.0               | 
	  +------------------------------------------+
	  | MDAC 2.1     | 21.1.3711.11              | 
	  +------------------------------------------+
	  | MDAC 2.5     | 25.0.4403.121             | 
	  +------------------------------------------+
	  | MDAC 2.6     | 5.0.2920.0                | 
	  +------------------------------------------+
	  | MDAC 2.7     | 27.0.7713.4               | 
	  +------------------------------------------+
	
	REFERENCES
	==========
	
	For additional information about how to distribute and install MDAC with a
	Visual Basic application, click the article numbers below to view the articles
	in the Microsoft Knowledge Base:
	
	  Q217754 HOWTO: Control Which MDAC Version the Package and Deployment Wizard
	  (PDW) Distributes
	
	  Q213846 INFO: Deploy Database Applications with the Package and Deployment
	  Wizard (PDW)
	
	  Q231943 INFO: Microsoft Data Access Components (MDAC) Release History
	
	Additional query words: ADO library
	
	======================================================================
	Keywords          : kbwizard kbAppSetup kbDeployment 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVB600 kbMDACSearch kbMDAC210 kbMDAC250 kbMDAC260 kbMDAC270
	Version           : :2.1,2.5,2.6,2.7,6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
