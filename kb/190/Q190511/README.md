---
layout: page
title: "Q190511: BUG: UserControl Containing Array of Controls Leaks Memory"
permalink: /kb/190/Q190511/
---

## Q190511: BUG: UserControl Containing Array of Controls Leaks Memory

{% raw %}

	Article: Q190511
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 5.0,6.0
	Operating System(s): 
	Keyword(s): kbVBp kbVBp500bug kbVBp600bug kbGrpDSVB kbDSupport kbControl
	Last Modified: 01-MAR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If a UserControl containing an array of controls is used, and one of the
	elements of the control array is assigned to an object, the following error may
	occur with repeated loading and unloading of the form that hosts the
	UserControl:
	
	  "Error 7: Out of memory"
	
	RESOLUTION
	==========
	
	There are two possible resolutions to this issue:
	
	- Create controls individually rather than in an control array.
	
	- Create a Public method in the user control that releases allocated memory and
	  then call the method from the Form that hosts the control array during the
	  Form Unload event. Note that you cannot do this in the control's Terminate
	  event because this event does not fire in this situation.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. We are researching this bug and will post new
	information here in the Microsoft Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	Sample code is provided in this article to illustrate both the problem and its
	workaround.
	
	To view the behavior of both the problem and the workaround, use a system tool
	that allows you to view available memory. On Windows NT 4.0 or Windows 2000,
	launch the Task Manager and watch the memory meter on the performance tab while
	running the application. On Windows 95, Windows 98, or Windows Me, use the
	Resource Meter utility.
	
	The problem happens in both the development environment and as a compiled
	application.
	
	Step-by-Step Example
	--------------------
	
	1. Start a new Standard EXE project in Visual Basic. Form1 is created by
	  default.
	
	2. Place a TextBox on Form1. Text1 is created by default. Now, enter the number
	  '3' in the Text property. This value represents the number of times the
	  called Form loads and unloads.
	
	3. Place a CommandButton (Command1) on Form1. Change Commad1's Caption property
	  to "Demonstrate Problem." NOTE: When this sample is completed, clicking this
	  button will demonstrate the problem.
	
	4. Place a second CommandButton (Command2) on Form1. Change Command2's Caption
	  property to "Workaround." NOTE: When this sample is completed, clicking this
	  button will demonstrate the workaround.
	
	5. Add the following code to the Form1 code window:
	
	        Option Explicit
	
	        ' This code demonstrates the problem.
	
	        Private Sub Command1_Click()
	           Dim i As Long, n As Long
	           n = Text1.Text
	           For i = 1 To n
	              Form2.Show
	              Unload Form2
	              Set Form2 = Nothing
	            Next i
	        End Sub
	
	        ' This code demonstrates the workaround.
	        Private Sub Command2_Click()
	           Dim i As Long, n As Long
	           n = Text1.Text
	           For i = 1 To n
	              Form3.Show
	              Unload Form3
	              Set Form3 = Nothing
	           Next i
	        End Sub
	
	6. From the Project menu, click Add User Control (UserControl1).
	
	7. Add three ComboBox controls to UserControl1 as a Control Array. To do this:
	  place a ComboBox from the Toolbox onto UserControl1, creating Combo1. Copy
	  Combo1 (CTRL+C) and then Paste it (CTRL+V). A dialog box will ask if you want
	  to create a Control Array; choose Yes. Then, paste a third ComboBox onto
	  UserControl1. Note that the Properties window now shows the three ComboBox
	  controls as Combo1(0), Combo1(1), and Combo1(2).
	
	8. Add the following code to the UserControl1 code window:
	
	        Option Explicit
	        Dim MyCombo As ComboBox
	
	        Private Sub UserControl_Initialize()
	           Set MyCombo = Combo1(0)
	        End Sub
	
	        Private Sub UserControl_Terminate()
	           MsgBox "Terminate"
	        End Sub
	
	9. From the Project menu, click Add User Control (UserControl2).
	
	10. Add three ComboBox controls to UserControl2 as a Control Array, as
	  demonstrated in step 7.
	
	11. Add the following code to the UserControl2 code window:
	
	        Option Explicit
	        Private MyCombo As ComboBox
	
	        Private Sub UserControl_Initialize()
	           Set MyCombo = Combo1(0)
	        End Sub
	
	        Public Sub CleanUp()
	           Set MyCombo = Nothing
	        End Sub
	
	12. From the Project menu, click Add Form (Form2).
	
	13. Place an instance of UserControl1 onto Form2. Note that you must close the
	  UserControl design window before you can place it onto Form2.
	
	14. Add a third form to the project (Form3). From the Project menu, select Add
	  Form.
	
	15. From the Toolbox, place UserControl2 onto Form3.
	
	16. Add the following code to the Form3 code window:
	
	        Option Explicit
	
	        Private Sub Form_Unload(Cancel As Integer)
	           UserControl21.Cleanup
	        End Sub
	
	17. Compile and Run your Project.
	
	To illustrate the problem, click on the "Demonstrate Problem" CommandButton. If
	you are using a system tool that allows you to view available memory, you will
	see that memory usage increases every time you click the Demonstrate Problem
	CommandButton. Memory is not recovered after unloading Form2 or after setting
	Form2 to Nothing. Notice that UserControl1's Terminate event does not fire in
	this situation (the message box does not display).
	
	To illustrate the workaround, click on the Workaround CommandButton. If you are
	using a system tool that allows you to view available memory, you will see that
	memory usage remains the same every time you click the Workaround CommandButton.
	Memory is recovered after unloading Form3. The workaround here is to release the
	memory from within UserControl2's CleanUp procedure, which is called during
	Form3's Form_Unload procedure.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbVBp kbVBp500bug kbVBp600bug kbGrpDSVB kbDSupport kbControl 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVB500 kbVB600
	Version           : :5.0,6.0
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
