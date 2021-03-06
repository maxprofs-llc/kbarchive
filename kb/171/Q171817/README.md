---
layout: page
title: "Q171817: FIX: UserControl Cannot Read ContainedControls in Visual FoxPro"
permalink: /kb/171/Q171817/
---

## Q171817: FIX: UserControl Cannot Read ContainedControls in Visual FoxPro

{% raw %}

	Article: Q171817
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 5.0
	Operating System(s): 
	Keyword(s): kbVBp500 kbVS97sp2fix kbGrpDSVBDB kbvbp500sp2fix
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Control Creation Edition for Windows, version 5.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 5.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0 
	- Microsoft Visual FoxPro for Windows, versions 5.0, 5.0a 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When a Visual Basic UserControl tries to read ContainedControls in Visual
	FoxPro, the following runtime error occurs:
	
	  "32768, "Application-defined or Object-defined error""
	
	RESOLUTION
	==========
	
	This problem is corrected with Visual Studio 97 Service Pack 2. However, any
	Visual Basic 5.0 ActiveX Controls built before the installation of the Service
	Pack will need to be recompiled.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug has been fixed in Visual Studio 97 Service
	Pack 2.
	
	For more information on the Visual Studio 97 Service Pack 2, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q170365 INFO: Visual Studio 97 Service Packs - What, Where, and Why
	
	For a list of the Visual Basic 5.0 bugs that were fixed in the Visual Studio 97
	Service Pack 2, please see the following article in the Microsoft Knowledge
	Base:
	
	  Q171554 INFO: Visual Basic 5.0 Fixes in Visual Studio 97 Service Pack 2
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a new ActiveX Control project.
	
	2. Name the UserControl "VBContainer" without the quotes.
	
	3. Name the Project "TestVBBuiltContainer" without the quotes.
	
	4. Set the ControlContainer property to True.
	
	5. Add the following code to VBContainer:
	
	        Public Property Let Caption(ByVal s As String)
	                 'See if ContainedControls works
	                 On Error Resume Next
	                 MsgBox "ContainedControls count =" _
	                    & UserControl.ContainedControls.Count
	                 If Err.Number <> 0 Then
	                    MsgBox "ContainedControls failed." & vbCrLf & _
	                       Err.Number & ": " & Err.Description
	                 End If
	              End Property
	
	              Private Sub UserControl_DblClick()
	                 Caption = "Hi"
	              End Sub
	
	6. From the File menu, select Make TestVBBuiltContainer.ocx.
	
	7. Start Visual FoxPro.
	
	8. In the Command Window, enter the following command:
	
	  Create Form
	
	9. From the Form Controls Toolbar, select the OLE Container Control.
	
	10. Place the OLE Container Control on the Form.
	
	11. Select Insert Control from the Insert Object dialog.
	
	12. Select TestVBBuiltContainer from the Object Type list, and click OK.
	
	13. In the Properties Window, try to set the Caption for the control. You will
	  receive the error described at the beginning of this article.
	
	14. Run the Form and double-click on the control. You will again receive the
	  error described at the beginning of this article.
	
	Additional query words: vfp
	
	======================================================================
	Keywords          : kbVBp500 kbVS97sp2fix kbGrpDSVBDB kbvbp500sp2fix 
	Technology        : kbVFPsearch kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVBA500Search kbVBA500 kbVB500 kbZNotKeyword3 kbVFP500 kbVFP500a
	Version           : 5.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
