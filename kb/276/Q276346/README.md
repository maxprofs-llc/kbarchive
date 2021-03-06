---
layout: page
title: "Q276346: FIX: SendKeys Function Locks Keyboard on Windows 2000"
permalink: /kb/276/Q276346/
---

## Q276346: FIX: SendKeys Function Locks Keyboard on Windows 2000

{% raw %}

	Article: Q276346
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 5.0,6.0,SP1
	Operating System(s): 
	Keyword(s): kbOSWin2000bug kbVBp kbVBp500 kbVBp600 kbGrpDSVB kbDSupport
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0, used with:
	   - the operating system: Microsoft Windows 2000 SP1 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0, used with:
	   - the operating system: Microsoft Windows 2000 SP1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When a Visual Basic program is running, the keyboard on your Windows 2000-based
	computer freezes.
	
	This problem can also occur if the application is hosted on a Terminal Server,
	and if the client is running Windows 2000. The following system event is logged
	on the Windows 2000-based computer:
	
	  Event Type:Error
	  Event Source:i8042prt
	  Event Category:None
	  Event ID:27
	  Description:
	  The operation on timed out (time out is configurable via the registry).
	
	CAUSE
	=====
	
	This problem is the result of a bug in the Windows 2000 keyboard driver, and
	only occurs in conjunction with the Visual Basic SendKeys function.
	
	RESOLUTION
	==========
	
	To resolve this problem on a Windows 2000-based computer that is not running
	Terminal Services, install Windows 2000 Service Pack 2 (SP2) from the following
	Microsoft Web site:
	
	  http://www.microsoft.com/windows2000/downloads/servicepacks/sp2/default.asp
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem. This fix may receive additional
	testing at a later time, to further ensure product quality. Therefore, if you
	are not severely affected by this problem, Microsoft recommends that you wait
	for the next Windows 2000 service pack that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Date         Time     Version         Size     File name
	  -----------------------------------------------------------
	  05/18/2000   07:17p   5.0.2195.2096   48,592   I8042prt.sys
	
	
	
	
	
	To unlock the keyboard manually, on the Start menu, point to Settings, and then
	click Control Panel. Click Keyboard, and then reset the Keyboard Refresh Rate.
	
	WORKAROUND
	==========
	
	There are also two programmatic workarounds to this problem:
	
	Workaround 1:
	
	Replace the SendKeys function with the keybd_event API function as follows:
	
	  Private Declare Sub keybd_event Lib "user32" (ByVal bVk As Byte,ByVal _
	   bScan As Byte, ByVal dwFlags As Long, ByVal dwExtraInfo As Long)
	
	  Const KEYEVENTF_KEYUP = &H2
	  Const VK_TAB = &H9
	
	  keybd_event VK_TAB, 0, 0, 0
	  keybd_event VK_TAB, 0, KEYEVENTF_KEYUP, 0
	
	Workaround 2:
	
	Replace the Sendkeys function with the PostMessage API function as follows:
	
	  Private Declare Function PostMessage Lib "user32" Alias "PostMessageA" _
	   (ByVal hwnd As Long, ByVal wMsg As Long, ByVal wParam As Long, _
	     ByVal lParam As Long) As Long
	
	  Const WM_KEYDOWN As Long = &H100
	  Const VK_TAB As Long = &H9
	  Dim retVal as long
	
	  retVal = PostMessage(Me.hwnd, WM_KEYDOWN, VK_TAB, 0)
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	MORE INFORMATION
	================
	
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. On a computer that is running Windows 2000, create a new Standard EXE project
	  in Visual Basic. Form1 is created by default.
	
	2. Set the Keypreview property of Form1 to True.
	
	3. Add six TextBoxes to Form1.
	
	4. Add the following code to the General Declarations section of Form1:
	
	  Private Sub Form_KeyDown(KeyCode As Integer, Shift As Integer)
	  If KeyCode = 13 Then
	       SendKeys "{tab}"
	  End If
	  End Sub
	
	5. Run the project.
	
	6. Press and hold down the Enter key on the numeric keypad, and note that the
	  keyboard locks in approximately five seconds.
	
	For additional information, click the article number below to view the article in
	the Microsoft Knowledge Base:
	
	  Q262798 PS/2 Keyboard/Mouse Not Recognized When Plugged Into Running Computer
	
	Additional query words: stops responding key pad board
	
	======================================================================
	Keywords          : kbOSWin2000bug kbVBp kbVBp500 kbVBp600 kbGrpDSVB kbDSupport 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2
	Version           : :5.0,6.0,SP1
	Hardware          : ALPHA x86
	Issue type        : kbprb
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
