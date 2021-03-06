---
layout: page
title: "Q180773: BUG: Closing a Form with Control Box &quot;X&quot; Only Hides Form"
permalink: /kb/180/Q180773/
---

## Q180773: BUG: Closing a Form with Control Box &quot;X&quot; Only Hides Form

{% raw %}

	Article: Q180773
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 2.0,2.11,3.0
	Operating System(s): 
	Keyword(s): kbToolkit kbVBp500bug kbOSWinCE100bug kbGrpDSVB
	Last Modified: 16-NOV-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows CE Toolkit for Visual Basic 6.0 
	- Microsoft eMbedded Visual Basic, version 3.0, used with:
	   - Microsoft Windows CE versions 2.0, 2.11 for the Handheld PC 
	   - Microsoft Windows CE version 2.11 for the Palm-size PC 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Closing a form with the control box "X" only hides the form. When showing the
	form a second time, values that that may have been changed on the form are not
	reset as you would expect. Properties that may have changed (including the form
	caption, text in textboxes, window position, and the hwnd of the form) remain
	the same.
	
	Although it can seem to be a related issue, it is important to note that in
	Visual Basic, it is expected behavior for form level variables to remain in
	memory when a form is closed using the control box "X."
	
	RESOLUTION
	==========
	
	The workaround is to include code to re-initialize the form in the form load
	event, which does fire when the form is re-shown after being closed via the
	control box "X."
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. We are researching this bug and will post new
	information here in the Microsoft Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a new Windows CE project in either Visual Basic or eMbedded Visual
	  Basic. Form1 is created by default.
	
	2. Add another form (Form2) to the project.
	
	3. Add a CommandButton (Command1) to Form1.
	
	4. Add a CommandButton (Command1) and a Textbox (Text1) to Form2.
	
	5. Paste the following code into the General Declarations section of Form1:
	
	        Private Sub Command1_Click()
	           Form2.Show
	        End Sub
	
	6. Paste the following code into the General Declarations section of Form2:
	
	        Private Sub Command1_Click()
	           Form2.Caption = "changed"
	           Text1.Text = "changed"
	           Command1.Caption = "changed"
	        End Sub
	
	7. Press the F5 key to run the project. Click the CommandButton on Form1 and
	  note that Form2 appears. Click the CommandButton on Form2 and note that
	  various values change.
	
	8. Move Form2 to another position. Click the Control box "X" on Form2 and note
	  that Form2 disappears.
	
	9. Click the "Show2" button on Form1 and note that the form reappears in the
	  position where it last was, with the form caption, command button caption,
	  and text box text values it had before being closed.
	
	Additional query words: vbce vbce6 wince evb
	
	======================================================================
	Keywords          : kbToolkit kbVBp500bug kbOSWinCE100bug kbGrpDSVB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword2 kbVBeMbSearch kbWinCETKVBSearch kbWinCESearch
	Version           : :2.0,2.11,3.0
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
