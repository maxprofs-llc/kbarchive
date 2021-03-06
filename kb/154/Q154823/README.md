---
layout: page
title: "Q154823: HOWTO: Determine the Size of the Desktop Area"
permalink: /kb/154/Q154823/
---

## Q154823: HOWTO: Determine the Size of the Desktop Area

{% raw %}

	Article: Q154823
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 
	Operating System(s): 
	Keyword(s): kbGrpDSVB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	- Microsoft Visual Basic Control Creation Edition for Windows, version 5.0 
	- Microsoft Visual Basic Learning Edition for Windows, version 5.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 5.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0 
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	It is often useful to determine the size and position of the display area taking
	the system tray into account. There are at least two methods to obtain this
	information: One requires the use of an OCX, while another makes a call to the
	Win32 API. This article demonstrates the step-by-step approaches to both of
	these methods.
	
	MORE INFORMATION
	================
	
	Method 1
	--------
	
	NOTE: In Microsoft Visual Basic 4.0, the SYSINFO.OCX control is in the
	\VB4\TOOLS\SYSINFO folder of the Visual Basic CD-ROM. It does not ship with the
	diskette version, and it is not automatically installed by Visual Basic Setup.
	Copy SYSINFO.OCX to the \WINDOWS\SYSTEM folder, and register it with
	REGOCX32.EXE. In Microsoft Visual Basic 5.0 and later, SYSINFO.OCX is installed
	by default.
	
	Use the SYSINFO.OCX control in your project. It has a number of useful
	properties, four of which disclose the size and position of the desktop area in
	twips. Follow the steps below:
	
	1. Start Visual Basic. Form1 is created by default.
	
	2. Add a Command button to Form1.
	
	3. From the Tools menu, choose Custom Controls and check the "Microsoft System
	  Info" component. If the component is not listed, click the browse button and
	  locate SYSINFO.OCX.
	
	4. Add a SysInfo control to Form1.
	
	5. Add the following code to the Command1_Click event:
	
	      Private Sub Command1_Click()
	
	        With SysInfo1
	          Print "WorkAreaLeft: " & .WorkAreaLeft / Screen.TwipsPerPixelX
	          Print "WorkAreaTop: " & .WorkAreaTop / Screen.TwipsPerPixelY
	          Print "WorkAreaWidth: " & .WorkAreaWidth / Screen.TwipsPerPixelX
	          Print "WorkAreaHeight: " & .WorkAreaHeight / Screen.TwipsPerPixelY
	        End With
	
	      End Sub
	
	6. Choose Start from the Run menu, or press the F5 key to run the project.
	
	7. Click the Command button to observe the size of the work area.
	
	Method 2
	--------
	
	The SystemParametersInfo function has many uses, including the ability to
	determine the size and position of the desktop. Follow the steps below:
	
	1. Start Visual Basic. Form1 is created by default.
	
	2. From the Insert menu, choose Module to add a single code module to the
	  project. Module1 is created by default.
	
	3. Add the following code to Module1:
	
	        Type RECT
	          Left As Long
	          Top As Long
	          Right As Long
	          Bottom As Long
	        End Type
	
	        Public Const SPI_GETWORKAREA = 48
	
	        Declare Function SystemParametersInfo Lib "user32" _
	          Alias "SystemParametersInfoA" (ByVal uAction As Long, _
	          ByVal uParam As Long, lpvParam As Any, ByVal fuWinIni As Long) _
	          As Long
	
	4. Add a Command button to Form1.
	
	5. Add the following code to the Command1_Click event:
	
	        Private Sub Command1_Click()
	
	          Dim lRet As Long
	          Dim apiRECT As RECT
	
	          lRet = SystemParametersInfo(SPI_GETWORKAREA, vbNull, apiRECT, 0)
	
	          If lRet Then
	            Print "WorkAreaLeft: " & apiRECT.Left
	            Print "WorkAreaTop: " & apiRECT.Top
	            Print "WorkAreaWidth: " & apiRECT.Right - apiRECT.Left
	            Print "WorkAreaHeight: " & apiRECT.Bottom - apiRECT.Top
	          Else
	            Print "Call to SystemParametersInfo failed."
	          End If
	
	        End Sub
	
	6. Choose Start from the Run menu, or press the F5 key to run the project.
	
	7. Click the Command button to observe the size of the work area.
	
	REFERENCES
	==========
	
	SYSINFO.HLP in the \TOOLS\SYSINFO directory on the Visual Basic 4.0 CD-ROM. In
	Visual Basic 5.0 and later, SYSINFO.HLP IS IN THE WINDOWS\HELP directory.
	
	Win32 SDK on the MSDN Visual Basic starter kit. This can be installed by running
	SETUP.EXE from the MSDN directory on the Visual Basic 4.0 CD-ROM.
	
	For more information, please see the following articles on the Microsoft
	Knowledge Base:
	
	  Q113702 : How to Control the Placement of Desktop Windows
	
	  Q97142 : How to Use SystemParametersInfo API for Control Panel Settings
	
	Additional query words: kbVBp400 kbVBp500 kbVBp600 KBWIN32SDK KBAPI kbVBp kbdsd kbDSupport
	
	======================================================================
	Keywords          : kbGrpDSVB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500Search kbVBA500 kbVBA600 kbVB500 kbVB600 kbVB400Search kbVB400 kbZNotKeyword3
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
