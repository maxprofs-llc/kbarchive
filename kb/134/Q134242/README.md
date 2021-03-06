---
layout: page
title: "Q134242: FIX: Label Text Box Accepts Too Many Characters Without Error"
permalink: /kb/134/Q134242/
---

## Q134242: FIX: Label Text Box Accepts Too Many Characters Without Error

{% raw %}

	Article: Q134242
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:3.0
	Operating System(s): 
	Keyword(s): kbbuglist kbfixlist
	Last Modified: 24-MAR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If you follow the process described in the next paragraph to enter a label
	longer than 255 characters, you end up losing the characters at the end of the
	label or the system may cause a fault and cause Visual FoxPro to quit.
	
	This problem occurs when on the Tools menu, you click Options. Then you click the
	Control tab, enter a string longer than 255 characters in the label, and click
	the check mark button. You may see an error message when you click the Set as
	Default button.
	
	CAUSE
	=====
	
	The Visual FoxPro version 3.0 program code that displays the keystrokes that
	enter the label string in the text box does not check for string length.
	
	WORKAROUND
	==========
	
	Enter only the characters needed for the label, and pre-determine that the text
	string has 255 or fewer characters.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products listed at
	the beginning of this article. This problem was corrected in Visual FoxPro 3.0b
	for Windows.
	
	MORE INFORMATION
	================
	
	A caption entered in a property sheet text box is limited to 255 characters.
	Characters beyond that number are not accepted in the text box.
	
	Steps to Reproduce Problem
	--------------------------
	
	1. Start Visual FoxPro.
	
	2. In the Command window, enter this command:
	
	     CREATE CLASSLIB mylib
	
	3. In the Command window enter the following command to bring up the Forms
	  Designer and its menu bar:
	
	     MODIFY FORM test
	
	4. On Tools menu, click Options.
	
	5. Click the Controls tab.
	
	6. Click the Add command button. Select mylib from the dialog box.
	
	7. Click the Label box and enter a character string longer than 255 characters.
	
	8. Click the check mark button to accept the label entry. The label replaces the
	  line mylib in the list box at the left, or the label in the list box is
	  empty.
	
	9. Click the Set as Default button at the bottom of the pageset. If this does
	  not cause a Win32s fault, go on to step 10.
	
	10. On the Forms Controls toolbar, click the Class Library tool. The label you
	  entered has become the name of the Class Library. It does not contain all of
	  the characters that were entered.
	
	Additional query words: VFoxWin fixlist3.00b buglist3.00
	
	======================================================================
	Keywords          :  kbbuglist kbfixlist
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300
	Version           : WINDOWS:3.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
