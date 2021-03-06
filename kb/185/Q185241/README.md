---
layout: page
title: "Q185241: BUG: Cannot Navigate Columns If a Row in a Grid is Disabled"
permalink: /kb/185/Q185241/
---

## Q185241: BUG: Cannot Navigate Columns If a Row in a Grid is Disabled

{% raw %}

	Article: Q185241
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:5.0,5.0a,6.0
	Operating System(s): 
	Keyword(s): kbnokeyword
	Last Modified: 11-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 5.0, 5.0a, 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When one of the rows in a grid is disabled, after selecting the disabled row and
	moving to the rightmost or leftmost column, the Right/Left arrow and the Tab
	keys cannot be used to switch from one column to the other. However, the mouse
	can be used to move from one column to another.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. We are researching this bug and will post new
	information here in the Microsoft Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create and populate a table as follows:
	
	        CREATE TABLE test (fld1 N(5), fld2 c(5))
	        INSERT INTO test VALUES (85000,"aaaaa")
	        INSERT INTO test VALUES (90000,"bbbbb")
	        INSERT INTO test VALUES (75000,"ccccc")
	        INSERT INTO test VALUES (60000,"ddddd")
	
	2. Create a form and add the table to its data environment.
	
	3. Drag and drop the table from the data environment onto the form to create a
	  grid.
	
	4. Place the following code in the grid's AfterRowColChange event:
	
	        IF test.fld1>80000
	           This.Columns(ncolindex).Enabled=.t.
	        ELSE
	           This.Columns(ncolindex).Enabled=.f.
	        ENDIF
	
	5. Run the form and use the Down Arrow key to move to the record that has 75000
	  in the first column.
	
	6. When the cell containing 75000 gets the focus, it is disabled.
	
	7. Use the RIGHT ARROW, LEFT ARROW, or TAB key to move to the leftmost or the
	  rightmost column in the row.
	
	8. Once the focus is in the leftmost or rightmost column, using the LEFT ARROW,
	  RIGHT ARROW, or TAB keys, try to move to some other column. Note that you
	  will not be able to move to another column.
	
	NOTE: You can use the Mouse to navigate from one column to another.
	
	Additional query words: vfoxwin kbvfp500 kbvfp600
	
	======================================================================
	Keywords          : kbnokeyword 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP500 kbVFP600 kbVFP500a
	Version           : WINDOWS:5.0,5.0a,6.0
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
