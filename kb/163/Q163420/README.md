---
layout: page
title: "Q163420: FIX: Running JOIN on Three or More Tables is Slow"
permalink: /kb/163/Q163420/
---

## Q163420: FIX: Running JOIN on Three or More Tables is Slow

{% raw %}

	Article: Q163420
	Product(s): Microsoft FoxPro
	Version(s): 5.0
	Operating System(s): 
	Keyword(s): kbusage kbvfp kbvfp500aFIX kbvfp500bugkbbuglist kbfixlist
	Last Modified: 12-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Running a SQL query that joins three or more tables in Visual FoxPro 5.0 is very
	slow. If Visual FoxPro 3.x is available for testing, this same query performs
	much faster by comparison. Using the new JOIN syntax with the SQL Select
	statement is also slow.
	
	CAUSE
	=====
	
	One or more of the tables have only one or only a few records that join with the
	other tables.
	
	RESOLUTION
	==========
	
	The query speed can usually be increased by using the new SQL Select syntax in
	Visual FoxPro 5.0 for JOINS in conjunction with the FORCE keyword.
	
	Using the sample SQL Select statements from step 3 under the Steps to Reproduce
	Behavior section below, the addition of the FORCE keyword makes the queries run
	much faster:
	
	        SELECT * FROM FORCE test1 ;
	         INNER JOIN test2 ON test2.id = test1.id ;
	         INNER JOIN test3 ON test3.id = test2.id
	
	        SELECT * FROM FORCE test1 ;
	         INNER JOIN (test2 INNER JOIN test3 ON test3.id = test2.id );
	         ON test2.id =test1.id
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products listed at
	the beginning of this article. This problem has been fixed in Visual FoxPro
	5.0a.
	
	MORE INFORMATION
	================
	
	This problem seems to occur when there is a join of three or more tables when
	there are only one or two records in one of the tables or there are only one or
	two records that have related records in the other tables. The tables also have
	to have a large number of records in them (30,000, 70,000 and 90,000). All of
	the table join scenarios that can exhibit the problem are not known.
	
	If the slow query is allowed to run, it may fill the computer's hard drive with a
	large temporary file and the following program error message may be received:
	
	  There is not enough disk space for c:\temp\12345678.tmp
	
	Steps to Reproduce Behavior
	---------------------------
	
	The following steps provide sample code that can be used to reproduce the
	problem. Press the Escape key to cancel the query in step 2 when desired.
	
	1. Place the code below in a program file and run it. The code creates three
	  tables that will take up about 6.6 MG of disk space:
	
	        CLOSE ALL
	        SET ECHO OFF
	        SET TALK OFF
	        CREATE TABLE test1 (ID C(15),Dummy C(15))
	        CREATE TABLE test2 (ID C(15),Dummy C(15))
	        CREATE TABLE test3 (ID C(15),Dummy C(15))
	        CLOSE ALL
	
	        WAIT WINDOW NOWAIT "filling test1"
	        USE test1
	        INDEX ON ID TAG ID
	        FOR x = 1 TO 71894
	        APPEND BLANK
	        REPLACE ID WITH SYS(2015)
	        NEXT
	        GO TOP
	        REPLACE NEXT 2 ID WITH "TEST"
	
	        WAIT WINDOW NOWAIT "filling test2"
	        USE test2
	        INDEX ON ID TAG ID
	        FOR x = 1 TO 30622
	        APPEND BLANK
	        REPLACE ID WITH SYS(2015)
	        NEXT
	        GO TOP
	        REPLACE NEXT 2 ID WITH "TEST"
	
	        WAIT WINDOW NOWAIT "filling test3"
	        USE test3
	        INDEX ON ID TAG ID
	        FOR x = 1 TO 90000
	        APPEND BLANK
	        REPLACE ID WITH SYS(2015)
	        NEXT
	        GO TOP
	        REPLACE NEXT 2 ID WITH "TEST"
	        CLOSE ALL
	
	2. Run the following query from a program file:
	
	        SELECT * FROM test1,test2,test3 ;
	         WHERE test1.id=test2.id AND test2.id=test3.id
	
	3. The following two SQL Select statements can also be used to reproduce the
	  problem using the sample data created in step 1 above:
	
	        SELECT * FROM test1 ;
	         INNER JOIN test2 ON test2.id = test1.id ;
	         INNER JOIN test3 ON test3.id = test2.id
	
	        SELECT * FROM test1 ;
	         INNER JOIN (test2 INNER JOIN test3 ON test3.id = test2.id );
	         ON test2.id =test1.id
	
	REFERENCES
	==========
	
	Microsoft Visual FoxPro "Developer's Guide" version 5.0, pages 214-215
	
	Additional query words:
	
	======================================================================
	Keywords          : kbusage kbvfp kbvfp500aFIX kbvfp500bug kbbuglist kbfixlist
	Technology        : kbVFPsearch kbAudDeveloper kbVFP500
	Version           : 5.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
