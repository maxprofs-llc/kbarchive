---
layout: page
title: "Q181946: HOWTO: Create a NetDDE Client and Server in Visual Basic"
permalink: /kb/181/Q181946/
---

## Q181946: HOWTO: Create a NetDDE Client and Server in Visual Basic

{% raw %}

	Article: Q181946
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 4.0,5.0
	Operating System(s): 
	Keyword(s): kbnokeyword kbVBp kbVBp400 kbVBp500 kbOSWin95 kbOSWin98 kbGrpDSVB kbDSupport kbOSWinME
	Last Modified: 27-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 5.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 5.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0 
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article demonstrates how to use NetDDE to communicate with a Microsoft
	Visual Basic application on a remote computer. This article assumes that you are
	familiar with DDE communications and demonstrates creating both the client and
	server applications in Visual Basic.
	
	MORE INFORMATION
	================
	
	In order to establish a link to a remote application, a DDE share must be
	created on the remote computer. A DDE share consists of a Share Name,
	Application name, and a Topic. Shares may be created and edited using the DDE
	Share Manager (DDESHARE.EXE), which may be found in the <WINNT\SYSTEM32>
	directory on NT 4.0. For Windows 95, Windows 98, Windows Me, and Windows For
	Workgroups, the Network DDE Share Manager can be found in the Windows for
	Workgroups Resource Kit.
	
	Creating the Visual Basic NetDDE Server
	---------------------------------------
	
	1. Start Visual Basic and create a new Standard EXE application. Form1 is
	  created by default.
	
	2. Place a Textbox (Text1) on Form1 and set the Text Property to "The DDE Server
	  is Running."
	
	3. Change the LinkMode Property of Form1 to "1 - Source."
	
	4. Select Project1 Properties from the Project menu, select the Make tab, and
	  then change the application title to DDESRV.
	
	5. Compile and save the application and name it DDESRV.EXE.
	
	6. Install the application on a computer on your network that you want to use as
	  the Server.
	
	Creating the DDE Share on the Server
	------------------------------------
	
	1. Start the DDE Share Manager Application on the Computer designated as the
	  Server. Select Run from the Windows Start menu, and then run DDESHARE.
	
	2. Select "DDE Shares" from the "Shares" menu. A list of shares that have
	  previously been set up will be displayed in the list box.
	
	3. Click the "Add a Share" button.
	
	4. Enter "DDETEST$" in the "Share Name" textbox.
	
	  NOTE: When creating the share name it is not necessary to place a trailing
	  "$," although it is conventional to do so.
	
	5. Enter the following values in the corresponding Application and Topic Text
	  boxes:
	
	                     Application Name              Topic Name
	                    -------------------          ---------------
	  oldstyle             DDESRV.DDE                    Form1
	  newsytle             DDESRV.OLE                    Form1
	  static               DDESRV                        Form1
	
	  NOTE: The DDESHARE utility for WFW/WIN95/WIN98 only supports defining one
	  Application and Topic name each. Use the static Application and Topic names
	  from the list above.
	
	6. Click OK to close the DDE Share Properties dialog.
	
	  IMPORTANT: Due to a bug in the DDE Share Utility, when exiting the DDE Share
	  application, a new serial number is created for the Share but is not updated
	  in the Trusted DDE Shares section of the registry; therefore, the next two
	  steps are very important.
	
	7. Select the DDETEST$ share in the list and click on the "Trust Share" button.
	
	8. Make sure that "Initiate to Application Enable" is selected and then click
	  the "SET" button.
	
	9. Press OK on both open dialogs and then exit the DDE Share Utility.
	
	Creating and Testing the Visual Basic NetDDE Client
	---------------------------------------------------
	
	1. Start a new Standard EXE project in Visual Basic. Form1 is created by
	  default.
	
	2. Add a CommandButton to Form1. Change the following properties:
	
	  Name:     cmdConnect
	  Caption:  Connect
	
	3. Add a Text box to Form1 and name it txtData.
	
	4. Paste the following code into the Declarations Section of Form1:
	
	  NOTE: Replace the <MACHINE NAME> with the appropriate computer name
	  where the DDE SRV application will be running.
	
	        Private Sub cmdConnect_Click()
	           txtData.linkMode = vbLinkNone
	           txtData.linkTopic = "\\<MACHINE NAME>\NDDE$|DDETEST$
	           txtData.LinkItem = "Text1"
	           txtData.LinkMode = vbLinkManual
	           txtData.LinkRequest
	        End Sub
	
	5. Start the DDESRV application on the Network computer acting as the DDE
	  Server.
	
	6. Press the F5 key to run this client within the Visual Basic 5.0 IDE.
	
	7. Click the Command button labeled "Connect" and note that the string "The DDE
	  Server is Running" appears within the txtData Text Box.
	
	REFERENCES
	==========
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q114089 : Using the Windows NT NetDDE Share Manager
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbnokeyword kbVBp kbVBp400 kbVBp500 kbOSWin95 kbOSWin98 kbGrpDSVB kbDSupport kbOSWinME 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVBA500 kbVB500 kbVB400Search kbVB400 kbVB16bitSearch
	Version           : :4.0,5.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
