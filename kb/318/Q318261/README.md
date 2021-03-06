---
layout: page
title: "Q318261: FIX: Grid Lines Assume the Windows Font Color"
permalink: /kb/318/Q318261/
---

## Q318261: FIX: Grid Lines Assume the Windows Font Color

{% raw %}

	Article: Q318261
	Product(s): Microsoft FoxPro
	Version(s): 7.0
	Operating System(s): 
	Keyword(s): kbContainer kbCtrl kbGrpDSFox kbDSupport kbCodeSnippet kbvfp700 _IK283 kbVFP700sp1fix
	Last Modified: 10-APR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 7.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The grid lines that surround a Visual FoxPro 7.0 grid assume the color of the
	Windows font. These lines should remain black regardless of the color that is
	assigned to the Windows font.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Visual FoxPro for
	Windows 7.0. For additional information, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q316964 How to Obtain the Latest Visual FoxPro for Windows 7.0 Service Pack
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Visual FoxPro for
	Windows 7.0.
	
	This problem was first corrected in Visual FoxPro for Windows 7.0 Service Pack 1.
	
	MORE INFORMATION
	================
	
	1. In Control Panel, double-click Display, and then click the Appearance tab.
	
	2. Click Advanced, and then change the Window color to white and the Font color
	  to blue.
	
	3. Paste the following code in a program (.prg) file named Test, and then run
	  the program from the Command window:
	
	  CREATE TABLE temp (f1 c(10))
	  INSERT INTO temp VALUES( "aaa")
	  oform=CREATEOBJECT("form")
	  oform.addobject("grid1","grid")
	  oform.grid1.recordsource="temp"
	  oform.grid1.visible=.t.
	  oform.show(1)
	
	Note that the grid lines that surround the grid object are blue. These lines
	should appear black.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbContainer kbCtrl kbGrpDSFox kbDSupport kbCodeSnippet kbvfp700 _IK283 kbVFP700sp1fix 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP700
	Version           : :7.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
