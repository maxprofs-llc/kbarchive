---
layout: page
title: "Q190068: BUG: Control Interface Wizard May Not Expose BackColor Property"
permalink: /kb/190/Q190068/
---

## Q190068: BUG: Control Interface Wizard May Not Expose BackColor Property

{% raw %}

	Article: Q190068
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kbwizard kbOSWinNT kbVBp600bug kbOSWin kbGrpDSVB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After you have used the ActiveX Control Interface Wizard to expose both the
	Appearance and BackColor properties of a control and you use the control in a
	project, any changes that you make to the BackColor property in the control's
	Properties window do not appear when you run the project.
	
	RESOLUTION
	==========
	
	You can manipulate the desired properties in code, or you can choose not to
	expose the Appearance property.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. We are researching this bug and will post new
	information here in the Microsoft Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	Create a UserControl Using the ActiveX Control Interface Wizard:
	
	1. Start Visual Basic 6.0, and open a new ActiveX Control project. Place a
	  command button on the UserControl.
	
	2. From the Add-Ins menu, select Add-In Manager and double-click "VB 6 ActiveX
	  Ctl Interface Wizard" in the Available Add-Ins column. Click OK to dismiss
	  the dialog.
	
	3. From the Add-Ins menu, select ActiveX Control Interface Wizard.
	
	  NOTE: If the Introduction screen for the ActiveX Control Interface Wizard
	  appears, click Next.
	
	4. In the Select Interface Member screen, choose the Appearance property from
	  the Available Names list on the left, click the ">" button to add it to
	  the Selected Names list on the right. Click Next.
	
	5. When the Create Custom Interface Members screen appears, click Next.
	
	6. In the Set Mapping window, under the Public Name list, select the Appearance
	  and BackColor properties for the UserControl member in the Control and Member
	  lists. Click Next.
	
	7. In the Set Attributes window, click Finish. Click Close to quit the ActiveX
	  Control Interface Wizard Summary dialog box.
	
	8. From the File menu, select Make Project1.ocx to compile the control.
	
	Test the UserControl in Another Project:
	
	1. Create a new Standard EXE project.
	
	2. Select Components from the Project menu. Add the UserControl to the toolbox
	  by selecting it from the list and clicking Apply.
	
	3. Place the UserControl from the toolbox onto Form1 in your Standard EXE
	  project.
	
	4. In the Properties window, change the BackColor Property of the ActiveX
	  Control to Red.
	
	5. Press the F5 key to run the project.
	
	RESULT: The UserControl appears with the design-time BackColor (based on the
	Appearance Property setting) instead of the BackColor (Red) that you chose in
	the Properties Window for that control.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbwizard kbOSWinNT kbVBp600bug kbOSWin kbGrpDSVB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVBA600 kbVB600
	Version           : WINDOWS:6.0
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
