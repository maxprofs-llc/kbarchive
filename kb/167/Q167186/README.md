---
layout: page
title: "Q167186: PRB: SET CENTURY ROLLOVER Ignores Setting of SET CENTURY OFF"
permalink: /kb/167/Q167186/
---

## Q167186: PRB: SET CENTURY ROLLOVER Ignores Setting of SET CENTURY OFF

{% raw %}

	Article: Q167186
	Product(s): Microsoft FoxPro
	Version(s): 5.0,5.0a
	Operating System(s): 
	Keyword(s): kbProgramming kbYear2000 kbvfp kbvfp500 kbvfp500a
	Last Modified: 14-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 5.0, 5.0a 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When using the ROLLOVER parameter of SET CENTURY, the SET CENTURY OFF setting is
	ignored. This results in a date display consisting of either two digits or four
	digits for the year portion of the date.
	
	RESOLUTION
	==========
	
	The reason for the display of the year in either a two- or four-digit format is
	to differentiate which century the date belongs to.
	
	It is possible to create a custom display format, which presents the date in the
	MM/DD/YY format along with another field to display which century.
	
	The following program demonstrates a sample method to do this.
	
	Step-by-Step Procedures
	-----------------------
	
	1. Save the following code as Daterev.prg:
	
	  *** Begin code ***
	        ON  KEY  LABEL f2 CLEAR EVENTS
	        ON KEY LABEL f3 DO refresh
	        SET CENTURY to 19 ROLLOVER 60
	        SET CENTURY off
	        dateform=CREATEOBJECT('form')
	        WITH dateform
	           .width=300
	           .height=65
	           .ADDOBJECT('text1','textbox')
	           WITH .text1
	              .format='K'
	              .inputmask='99/99/99'
	              .left=1
	              .top=10
	              .width=60
	              .value=DTOC(date())
	              .visible=.t.
	           ENDWITH   && text1
	           .ADDOBJECT('label1','label')
	           WITH .label1
	              .top=50
	              .left=90
	              .width=120
	              .fontbold=.t.
	              .caption="Press <F2> to exit form"
	              .visible=.t.
	           ENDWITH   && label1
	           .ADDOBJECT('label2','label')
	           WITH .label2
	              .caption="Year of date shown is  "+ ;
	                 ALLTRIM(STR(YEAR(CTOD(dateform.text1.value))))
	              .top=32
	              .left=10
	              .width=160
	              .fontbold=.t.
	              .visible=.t.
	           ENDWITH   && label2
	           .ADDOBJECT('label3','label')
	           WITH .label3
	              .caption='Press <f3> to refresh after entering new date'
	              .top=10
	              .left=65
	              .width=250
	              .fontbold=.t.
	              .visible=.t.
	           ENDWITH   && label3
	           .show
	        ENDWITH   && dateform
	        READ EVENTS
	        ON KEY LABEL f2
	        ON KEY LABEL f3
	
	        PROCEDURE refresh
	           dateform.label2.caption="Year of date shown is: "+ ;
	               ALLTRIM(STR(YEAR(CTOD(dateform.text1.value))))
	           dateform.refresh
	        RETURN
	        *** End code ***
	
	2. Run the program, and note that the four-digit display of the date shown is
	  shown below the text box.
	
	3. Enter a valid date for the 21st century, such as "02/12/55."
	
	4. Press the F3 key to refresh the display, and note that in the line below the
	  text box, the year is shown as "2055."
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	The ROLLOVER clause of SET CENTURY command permits ease of entering dates that
	may cross century boundaries. For example:
	
	  SET CENTURY to 19 ROLLOVER 60
	
	This means that when a two-digit value for a year "60" and greater falls within
	the 21st century, two-digit values less than 60 fall into the 20th century.
	
	Using the information above, "02/15/97" is deemed the year "1997." And "02/15/55"
	is interpreted as the year 2055.
	
	To better understand the implications of the ROLLOVER parameter, the following
	program demonstrates its effect on how dates are displayed.
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Save the following code as Formdate.prg:
	
	  *** Begin code ***
	        ON  KEY  LABEL f2 CLEAR EVENTS
	        SET CENTURY to 19 ROLLOVER 60
	        SET CENTURY off
	        dateform=CREATEOBJECT('form')
	        WITH dateform
	           .width=120
	           .height=65
	           .ADDOBJECT('text1','textbox')
	           WITH .text1
	              .format='K'
	              .left=35
	              .top=10
	              .width=75
	              .value=date()
	              .visible=.t.
	           ENDWITH   && text1
	           .ADDOBJECT('label1','label')
	           WITH .label1
	              .top=35
	              .left=1
	              .width=120
	              .fontbold=.t.
	              .caption="Press <F2> to exit form"
	              .visible=.t.
	           ENDWITH   && label1
	           .show
	        ENDWITH   && dateform
	        READ EVENTS
	        ON KEY LABEL f2
	        *** End code ***
	
	2. Run the program, and note that the current date appears with two digits for
	  year.
	
	3. In the text box, enter a date with a year less than 60, such as 01/10/56. As
	  soon the "56" is entered, the year is displayed as "2056."
	
	4. Enter a date with a year greater than 60, such as 12/01/99, and note that the
	  date is shown with only the last two digits of the year omitting the century.
	
	REFERENCES
	==========
	
	For more information about SET CENTURY, search for CENTURY in the Visual FoxPro
	Help file.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbProgramming kbYear2000 kbvfp kbvfp500 kbvfp500a 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP500 kbVFP500a
	Version           : :5.0,5.0a
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
