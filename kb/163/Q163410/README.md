---
layout: page
title: "Q163410: ODE97: Creating Run-Time Apps for MS Excel, Word, or PowerPoint"
permalink: /kb/163/Q163410/
---

## Q163410: ODE97: Creating Run-Time Apps for MS Excel, Word, or PowerPoint

{% raw %}

	Article: Q163410
	Product(s): Microsoft Access Distribution Kit
	Version(s): 
	Operating System(s): 
	Keyword(s): kbsetup
	Last Modified: 01-JUL-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Office 97 Developer Edition 
	-------------------------------------------------------------------------------
	
	Moderate: Requires basic macro, coding, and interoperability skills.
	
	
	SUMMARY
	=======
	
	There may be times you want to create run-time applications that include
	Microsoft Excel spreadsheets, Microsoft PowerPoint presentations, or Microsoft
	Word documents using the ODE Setup Wizard. This article demonstrates how to
	create custom applications that you can distribute to other users who don't have
	Microsoft Excel, Word, or PowerPoint on their computers. One way this can be
	done is by adding the application's viewer files to the Setup Wizard program
	when you are creating your distribution disks.
	
	NOTE: Using the methods described in this article, your users will only be able
	to view your Microsoft Excel spreadsheets, Word documents, or PowerPoint
	presentations. They will not be able to make any modifications to the files.
	
	MORE INFORMATION
	================
	
	To create a custom application that you can distribute to other users, include
	the correct viewer files for the particular application in the ODE Setup Wizard.
	The files you will need to add to the Setup wizard depends on the types of files
	you want to distribute.
	
	For example, if you want to distribute Microsoft Excel spreadsheets, you will
	need to obtain the files for the Microsoft Excel Viewer. The Microsoft Excel
	viewer enables users to view Microsoft Excel spreadsheets without having
	Microsoft Excel on their computers. This viewer is available on the Microsoft
	web at:
	
	  http://www.microsoft.com/office/excel/downloads/default.htm
	
	If you want to distribute PowerPoint presentations or Word documents, you can
	obtain the Word and PowerPoint viewers from the ValuPack folder that is included
	in the Microsoft Office 97, Professional Edition package. The viewer files are
	in the subfolder Ppt4view for the PowerPoint files and Wordview for the Word
	files.
	
	Creating a Distributable Application for Microsoft Excel Files
	--------------------------------------------------------------
	
	To create a distributable custom Setup program for your Microsoft Excel
	spreadsheets, do the following:
	
	1. Download the Microsoft Excel Viewer files from the Microsoft Web Site at:
	
	  http://www.microsoft.com/office/excel/downloads/default.htm
	
	2. After you have run the setup file xlViewer.exe to install the Microsoft Excel
	  viewer on your computer, start the ODE Setup Wizard program.
	
	3. In the ODE Setup wizard, on the Add files screen, add the following files and
	  any Microsoft Excel spreadsheet files you want to distribute to the List Of
	  Files box:
	
	  - XL5EN32.OLB
	  - XLINTL32.DLL
	  - XLKEY32.DLL
	  - XLVIEW.EXE
	  - XLVIEW1.REG
	  - XLVIEW2.REG
	  - XLVIEW3.REG
	
	  NOTE: These files can be found in the folder where you installed the Microsoft
	  Excel viewer files.
	
	4. Select Xlview.exe in the List Of Files box, and then click to select the "Set
	  as Application's Main File" check box. Click Next.
	
	5. On the Add Shortcuts screen, click Add, and then type a description for your
	  shortcut in the Description box. Leave the default "I would like to use a
	  wizard-provided command line" option selected on the General Shortcut
	  Properties tab. Click Next three times.
	
	6. In the "What is the name of your application" box, type the name you want to
	  give to your new Microsoft Excel viewer application. Fill in the rest of the
	  information as needed for your particular application. Click Next twice.
	
	7. On the screen marked "Where do you want the Setup Wizard to copy the files
	  for your custom Setup program," accept the default for the folder your disk
	  images will be copied to in the "The Setup Wizard creates a folder for each
	  of your disk images within the folder you specify" box.
	
	8. Select the option for the type(s) of distribution disks you want to create.
	  Click Finish.
	
	At this point, the ODE Setup Wizard creates the disk images for your application.
	Once the disk images are created, you can run your custom Setup program on any
	computer. Users of your spreadsheets who do not have Microsoft Excel can view
	them through the Microsoft Excel viewer.
	
	For more information about using the Microsoft Excel viewer, read the following
	files that are installed when you download xlViewer.EXE in the folder where you
	have installed Xlview.exe:
	
	- LICENSE.TXT
	
	- README.TXT
	
	For additional information about the Microsoft Excel Viewer, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q141224 What Is the Microsoft Excel Viewer for Windows 95?
	
	
	Creating a Distributable Application for Microsoft Word Files
	-------------------------------------------------------------
	
	To create a distributable custom Setup program for your Microsoft Word documents,
	do the following:
	
	1. Install the Microsoft Word Viewer included on the Microsoft Office 97,
	  Professional Edition compact disc in the ValuPack folder. The Word files are
	  located in the WordView subfolder. The Word Viewer can be installed by
	  double-clicking the file WD95VW71.EXE.
	
	2. After you have install the Microsoft Word Viewer on your computer, start the
	  ODE Setup Wizard program.
	
	3. In the ODE Setup wizard, on the Add files screen, add the following files and
	  any Microsoft Word documents you want to distribute to the List Of Files box:
	
	  - SDM95.DLL
	  - TTEMB32V.DLL
	  - WINTL32V.DLL
	  - WORDVIEW.EXE
	
	4. Select WORDVIEW.EXE in the List Of Files box, and then click to select the
	  "Set as Application's Main File" check box. Click Next.
	
	5. On the Add Shortcuts screen, click Add, and then type a description for your
	  shortcut in the Description box. Leave the default "I would like to use a
	  wizard-provided command line" option selected on the General Shortcut
	  Properties tab. Click Next three times.
	
	6. In the "What is the name of your application" box, type the name you want to
	  give to your new Microsoft Word viewer application. Fill in the rest of the
	  information as needed for your particular application. Click Next twice.
	
	7. On the screen marked "Where do you want the Setup Wizard to copy the files
	  for your custom Setup program," accept the default for the folder your disk
	  images will be copied to in the "The Setup Wizard creates a folder for each
	  of your disk images within the folder you specify" box.
	
	8. Select the options for the type(s) of distribution disks you want to create.
	  Click Finish.
	
	At this point, the ODE Setup Wizard creates the disk images for your application.
	Once the disk images are created, run your custom Setup program on any computer.
	Your users that do not have Word installed on their computers can view your Word
	documents using the Word Viewer.
	
	For more information about using the Microsoft Word viewer, read the following
	files that are copied to your WordView folder when you install the Word Viewer
	program:
	
	- INSTALL.TXT
	
	- LICENSE.TXT
	
	- README.TXT
	
	For additional information about the Microsoft Word Viewer, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q136593 How to Obtain Word Viewer for Windows 95
	
	
	Creating a Distributable Application for Microsoft PowerPoint Files
	-------------------------------------------------------------------
	
	To create a distributable custom Setup program for your Microsoft PowerPoint
	presentations, do the following:
	
	1. Install the Microsoft PowerPoint Viewer included on the Microsoft Office 97,
	  Professional Edition compact disc in the ValuPack folder. The PowerPoint
	  files are located in the Ppt4view subfolder. The PowerPoint Viewer can be
	  installed by double-clicking the file Vsetup.exe.
	
	2. After you have install the Microsoft PowerPoint Viewer on your computer,
	  start the ODE Setup Wizard program.
	
	3. In the ODE Setup Wizard, on the Add files screen, add the following files and
	  any Microsoft PowerPoint presentations you want to distribute to the List Of
	  Files box:
	
	  - PP7TRANS.DLL
	  - PPTVIEW.DLL
	  - PPTVIEW.EXE
	
	  NOTE: These files can be found in the Pptview folder.
	
	4. Select PPTVIEW.EXE in the List Of Files box, and then click to select the
	  "Set as Application's Main File" check box. Click Next.
	
	5. On the Add Shortcuts screen, click Add, and then type a description for your
	  shortcut in the Description box. Leave the default "I would like to use a
	  wizard-provided command line" option selected on the General Shortcut
	  Properties tab. Click Next three times.
	
	6. In the "What is the name of your application" box, type the name you want to
	  give to your new Microsoft PowerPoint viewer application. Fill in the rest of
	  the information as needed for your particular application. Click Next twice.
	
	7. On the screen marked "Where do you want the Setup Wizard to copy the files
	  for your custom Setup program," accept the default for the folder your disk
	  images will be copied to in the "The Setup Wizard creates a folder for each
	  of your disk images within the folder you specify" box.
	
	8. Select the options for the type(s) of distribution disks you want to create.
	  Click Finish.
	
	At this point, the ODE Setup Wizard creates the disk images for your application.
	Once the disk images are created, run your custom Setup program on any computer.
	Your users can view your PowerPoint presentations using the PowerPoint Viewer.
	
	For more information about using the Microsoft PowerPoint viewer, open the
	Valupk8.hlp file located in the ValuPack folder on your Microsoft Access 97 or
	Microsoft Office 97 compact disc.
	
	REFERENCES
	==========
	
	For more information about creating custom application using the ODE Setup
	Wizard, search the Help Index for "Setup Wizard, creating Setup programs," or
	ask the Microsoft Access 97 Office Assistant.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbsetup 
	Technology        : kbOfficeSearch kbAudDeveloper kbOffice97Search kbOffice97 kbOffice97DevSearch
	Version           : :
	Hardware          : x86
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
