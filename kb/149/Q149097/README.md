---
layout: page
title: "Q149097: BUG: Data Control Validate Event Not Fired on Unloading Form"
permalink: /kb/149/Q149097/
---

## Q149097: BUG: Data Control Validate Event Not Fired on Unloading Form

{% raw %}

	Article: Q149097
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 4.00 | 4.00
	Operating System(s): 
	Keyword(s): kbbuglist
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A form containing a bound Data Control disables the Validate event when the form
	is unloaded.
	
	STATUS
	======
	
	Microsoft has confirmed this to be an issue in the Microsoft products listed at
	the beginning of this article. Microsoft is researching this issue and will post
	new information here in the Microsoft Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	The following are steps to reproduce this behavior. The Cancel property is set
	to true in the Unload event of the form to prevent the form from unloading. When
	you edit a record and then unload the form, the validate event, containing a
	beep instruction, executes only one more time.
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Start 16-bit or 32-bit Visual Basic 4.0, or if it is already running, click
	  New Project on the File menu.
	
	2. Add the following controls and set the following properties:
	
	     Control              Default Name   Property              Value
	     --------------------------------------------------------------------
	
	     Data Control            Data1       Database Name         BIBLIO.MDB
	                                         RecordSource          Authors
	
	     TextBox Control         Text1       DataSource            Data1
	                                         DataField             Author
	
	     Command Button          Command1
	
	3. Copy the following code to the Code window of the Form1 form:
	
	        Option Explicit
	
	        Private Sub Command1_Click()
	           Unload Me
	        End Sub
	
	        Private Sub Data1_Validate(Action As Integer, Save As Integer)
	           Beep
	        End Sub
	
	        Private Sub Form_Unload(Cancel As Integer)
	           'The next line stops the form from being unloaded
	           Cancel = True
	        End Sub
	
	4. On the Run menu, click Start or press the F5 key to start the program. Scroll
	  through the records and click the command button. Note that a beep occurs
	  with each action.
	
	5. Edit a record and click the command button. Scroll through the records and
	  note the a beep occurs only once. Scrolling through the records or clicking
	  the command button does not execute the Validate event.
	
	Additional query words: 4.00 vb4win vb4all
	
	======================================================================
	Keywords          :  kbbuglist
	Technology        : kbVBSearch kbAudDeveloper kbVB400Search kbVB400 kbVB16bitSearch
	Version           : 4.00 | 4.00
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
