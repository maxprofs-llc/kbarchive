---
layout: page
title: "Q136921: Guidelines for Creating Unique and Sequential Keys"
permalink: /kb/136/Q136921/
---

## Q136921: Guidelines for Creating Unique and Sequential Keys

{% raw %}

	Article: Q136921
	Product(s): Microsoft FoxPro
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 20-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	You can create unique and sequential keys in Visual FoxPro by using two of
	Visual FoxPro's new features: Stored Procedures and Default Values.
	
	MORE INFORMATION
	================
	
	To see an example showing how to create unique and sequential keys, please look
	at the TasTrade sample application located in the Vfp\Samples\Mainsamp
	directory. In this sample, the NewID() stored procedure has been written and
	stored in the TasTrade database. The following text is taken from the "Behind
	the Scenes" feature of the Tastrade sample:
	
	The NewID() stored procedure creates unique IDs in the system. It returns the
	default value for the primary keys for the Supplier, Products, Employee,
	Category, Shippers, and Orders tables.
	
	Code in NewID() opens Setup.dbf, looks for table alias in the Key_name field,
	reads the current value of the Value field, increments it by 1, and then writes
	it back to Setup.dbf. The value that was read from the Value field before
	incrementing is then returned as the primary key value for a record.
	
	Note that the NewID() stored procedure is also designed to accept an alias as a
	parameter. The same technique could then be used to maintain incrementing values
	that were not being used as primary keys. An example of this is the order_number
	record, which is used to generate order numbers for the Orders table.
	
	You can modify stored procedures by first opening the database with the OPEN
	DATABASE command, and then using the MODIFY PROCEDURES command to bring up an
	editing window. Alternatively, you can use the MODIFY DATABASE command, and then
	click the Stored Procedures button on the toolbar.
	
	The code for NewID() is as follows:
	
	     FUNCTION NewID(tcAlias)
	       LOCAL lcAlias, ;
	             lcID, ;
	             lcOldReprocess, ;
	             lnOldArea
	
	       lnOldArea = SELECT()
	
	       IF PARAMETERS() < 1
	         lcAlias = UPPER(ALIAS())
	       ELSE
	         lcAlias = UPPER(tcAlias)
	       ENDIF
	
	       lcID = ""
	       lcOldReprocess = SET('REPROCESS')
	
	       *-- Lock until user presses Esc
	       SET REPROCESS TO AUTOMATIC
	
	       IF !USED("SETUP")
	         USE tastrade!setup IN 0
	       ENDIF
	       SELECT setup
	
	       IF SEEK(lcAlias, "setup", "key_name")
	         IF RLOCK()
	           lcID = setup.value
	           REPLACE setup.value WITH ;
	                   STR(VAL(ALLT(lcID)) + 1, LEN(setup.value))
	           UNLOCK
	         ENDIF
	       ENDIF
	
	       SELECT (lnOldArea)
	       SET REPROCESS TO lcOldReprocess
	
	       RETURN lcID
	     ENDFUNC
	
	Additional query words: VFoxWin
	
	======================================================================
	Keywords          :  
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300
	
	=============================================================================
	

{% endraw %}
