---
layout: page
title: "Q198043: WD97: Extra Paragraph Mark Above Include Field at Top of Doc"
permalink: /kb/198/Q198043/
---

## Q198043: WD97: Extra Paragraph Mark Above Include Field at Top of Doc

{% raw %}

	Article: Q198043
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbfield winword word97 kblayout kbtable
	Last Modified: 14-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If you select the Link to File check box and insert a file that starts with a
	table at the beginning of a document, Word adds a paragraph mark to the
	beginning of the document. You cannot delete this additional paragraph mark.
	
	NOTE: The additional paragraph mark is not displayed when the Field Codes option
	is selected.
	
	If you insert a file that begins with a table at the start of a document and do
	not select the Link to File check box, Word does not add the paragraph mark to
	the beginning of the document.
	
	WORKAROUND
	==========
	
	If the extra paragraph mark disrupts the page layout of your document, you can
	change the paragraph line spacing setting to 0.01 inch by following these
	steps:
	
	1. On the Format menu, click Paragraph. Select Exactly in the Line Spacing box,
	  and type "0.01"" (without the quotation marks). Note the inches mark.
	
	2. Click OK.
	
	MORE INFORMATION
	================
	
	To insert a file into a Word document, use either of the following methods.
	
	Method 1: Use the Menus to Link to the File
	-------------------------------------------
	
	1. On the Insert menu, click File.
	
	2. Select the file in the File Name box.
	
	3. Select the Link to File check box as appropriate.
	
	4. Click OK.
	
	Method 2: Type the IncludeText Field
	------------------------------------
	
	1. Press CTRL+F9 to insert field braces into your document.
	
	2. Type "INCLUDETEXT filename" (without the quotation marks) inside the braces.
	
	  where filename is the path and file name of your document.
	
	3. Turn the field codes off by pressing ALT+F9.
	
	Additional query words: linked extra 8.0 8.00
	
	======================================================================
	Keywords          : kbfield winword word97 kblayout kbtable 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
