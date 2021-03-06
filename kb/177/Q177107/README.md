---
layout: page
title: "Q177107: ODE97: Displaying Context-Sensitive Help for What'sThis Button"
permalink: /kb/177/Q177107/
---

## Q177107: ODE97: Displaying Context-Sensitive Help for What'sThis Button

{% raw %}

	Article: Q177107
	Product(s): Microsoft Access Distribution Kit
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbdta
	Last Modified: 23-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Access 97 
	- Microsoft Office 97 Developer Edition 
	-------------------------------------------------------------------------------
	
	
	Advanced: Requires expert coding, interoperability, and multiuser skills.
	
	SUMMARY
	=======
	
	You can provide context-sensitive help for a What's This button on the Title bar
	of your form by using the WhatsThisButton property. When this property is set to
	True, the mouse pointer changes to the What's This state (arrow with a question
	mark) and the topic displayed is identified by the WhatsThisHelpID property of
	the control that the user clicks.
	
	This article demonstrates how to display context-sensitive help for the
	WhatsThisHelp property by using Help to open a pop-up window provided by Windows
	95 Help.
	
	MORE INFORMATION
	================
	
	To display context-sensitive help that appears when a user clicks the What's
	This button and drops it on an object on your form or report, follow these
	steps:
	
	1. Create your Help topics in Microsoft Word or another word processor. For more
	  information about creating your topic files in Microsoft Word, please see the
	  following articles in the Microsoft Knowledge Base:
	
	  Q177116 ODE97: How to Create Context-Sensitive Help for a Microsoft Access
	  Database
	
	  Q175491 ODE97: Step-by-Step Example of Creating/Compiling a Help File
	
	  Q163939 ODE97: Help Workshop Help Topics Contents
	
	  Q171958 ODE97: Tips for Creating and Compiling Your Windows Help File
	
	2. Use Microsoft Help Workshop to compile your Help topics.
	
	3. Open the form that contains the objects for which you want to provide What's
	  This help information.
	
	4. On the View menu, click Properties to display the form's properties box.
	
	5. In the Form Properties box, change the MinMaxButtons property to None and the
	  WhatsThisButton property to Yes.
	
	6. In the HelpFile property, type the name for the Help file that contains your
	  Help topics.
	
	  NOTE: Copy this file to your Windows Help folder so that Microsoft Access will
	  be able to find it.
	
	7. In the HelpContextID property, type the number that you linked the Help topic
	  to in Microsoft Help Workshop.
	
	  NOTE: To display the Help topic in a pop-up window, put a minus sign (-)
	  before the number.
	
	8. Repeat step 7 for each control on the form that you want to link to a Help
	  topic.
	
	9. Open the form in Form view, click the What's This button, and drag it to one
	  of your controls.
	
	  Note that the Help topic information appears.
	
	REFERENCES
	==========
	
	For more information about creating What's This help information, search the
	Help Index for "WhatsThisHelp property," or ask the Microsoft Access 97 Office
	Assistant.
	
	Additional query words: ODE whatsthis whats what s this button
	
	======================================================================
	Keywords          : kbdta 
	Technology        : kbOfficeSearch kbAudDeveloper kbAccessSearch kbAccess97 kbOffice97Search kbAccess97Search kbOffice97 kbOffice97DevSearch
	Version           : WINDOWS:97
	Hardware          : x86
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
