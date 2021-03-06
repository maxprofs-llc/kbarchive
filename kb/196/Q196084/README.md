---
layout: page
title: "Q196084: HOWTO: Retrieve Foreign Key Information from SQL Server"
permalink: /kb/196/Q196084/
---

## Q196084: HOWTO: Retrieve Foreign Key Information from SQL Server

{% raw %}

	Article: Q196084
	Product(s): Microsoft FoxPro
	Version(s): MACINTOSH:3.0b; WINDOWS:2.5,3.0,3.0b,5.0,5.0a,6.0
	Operating System(s): 
	Keyword(s): kbClient KbClientServer kbDatabase kbSQL kbvfp kbvfp300b kbvfp500 kbvfp500a kbvfp600 kb
	Last Modified: 27-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 3.0b, 5.0, 5.0a, 6.0 
	- Microsoft Visual FoxPro for Macintosh, version 3.0b 
	- Microsoft Data Access Components version 2.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When creating remote views using SQL Server tables as the data source, Visual
	FoxPro automatically sets the KeyField property to .T. for columns that are
	included in a primary index key. You can use the SQL Server stored procedure,
	sp_pkeys, to return primary key information from SQL Server. The sp_pkeys stored
	procedure, however, does not return information regarding the relationship(s)
	between tables.
	
	In some circumstances, a developer may want to retrieve the foreign key
	information programmatically to provide greater detail of the relationship
	between tables. This article shows how to use the stored procedure sp_fkeys to
	return foreign key information from SQL Server.
	
	MORE INFORMATION
	================
	
	The sp_fkeys stored procedure returns a cursor with logical foreign key
	information for the current environment. This procedure shows foreign key
	relationships including disabled foreign keys. The sp_fkeys stored procedure is
	equivalent to SQLForeignKeys in ODBC. The results returned are ordered by
	FKTABLE_QUALIFIER, FKTABLE_OWNER, FKTABLE_NAME, and KEY_SEQ.
	
	The columns returned by sp_fkeys follow:
	
	  Column Name          Description
	  -----------------------------------------------------------------------
	
	  PKTABLE_QUALIFIER    Name of the table (with the primary key) qualifier.
	                       This column represents the database name for the
	                       table with a PRIMARY KEY constraint and may be
	                       NULL.
	
	  PKTABLE_OWNER        Name of the table (with the primary key) owner.
	                       This column represents the name of the database
	                       user that created the table (with a PRIMARY KEY
	                       constraint) and always returns a value.
	
	  PKTABLE_NAME         Name of the table (with the primary key). This
	                       column represents the table name (with a PRIMARY
	                       KEY constraint) as listed in the sysobjects table
	                       and always returns a value.
	
	  PKCOLUMN_NAME        Name of the primary key column(s), for each column
	                       of the TABLE_NAME returned. This column represents
	                       the column name as listed in the syscolumns table
	                       and always returns a value.
	
	  FKTABLE_QUALIFIER    Name of the table (with a foreign key) qualifier.
	                       This column represents the database name for the
	                       table (with a FOREIGN KEY constraint) and may be
	                       NULL.
	
	  FKTABLE_OWNER        Name of the table (with a foreign key) owner. This
	                       column represents the name of the database user
	                       that created the table (with a FOREIGN KEY
	                       constraint) and always returns a value.
	
	  FKTABLE_NAME         Name of the table (with a foreign key). This column
	                       represents the table name as listed in the
	                       sysobjects table (with a FOREIGN KEY constraint)
	                       and always returns a value.
	
	  FKCOLUMN_NAME        Name of the foreign key column(s), for each column
	                       of the TABLE_NAME returned. This column represents
	                       the column name as listed in the syscolumns table
	                       and always returns a value.
	
	  KEY_SEQ              Sequence number of the column in a multicolumn
	                       primary key. This field always returns a value.
	
	  UPDATE_RULE          Action applied to the foreign key when the SQL
	                       operation is UPDATE. SQL Server returns 1 for this
	                       column.
	
	  DELETE_RULE          Action applied to the foreign key when the SQL
	                       operation is DELETE. SQL Server returns 1 for this
	                       column.
	
	  FK_NAME              Foreign key identifier. This is the FOREIGN KEY
	                       constraint name, and may be NULL if not applicable
	                       to the data source.
	
	  PK_NAME              Primary key identifier. This is the PRIMARY KEY
	                       constraint name, and may be NULL if not applicable
	                       to the data source.
	
	Create a program named SP_fkeys.prg using the following code:
	
	     * Substitute the server name.
	     #DEFINE Connect_String 'DRIVER={SQL Server};SERVER=MY_SERVER;' + ;
	        'DATABASE=PUBS;UID=sa;PWD='
	     * Create a cursor to store information.
	     CREATE CURSOR SQLKeys (Parent_Qualifier c(128), Parent_Owner c(128), ;
	        Parent_Table_Name c(128), Parent_Column_Name c(128), ;
	        Foreign_Qualifier c(128), Foreign_Owner c(128), ;
	        Foreign_Table_Name c(128), Foreign_Column_Name c(128), ;
	        Key_Seq I, FK_NAME c(128), PK_Name c(128))
	     * Connect to SQL Server.
	     gnConnHandle=SQLSTRINGCONN(Connect_String)
	     IF gnConnHandle>0
	        * Get the tables available on SQL Server.
	        SQLConnTables=SQLTABLES(gnConnHandle)
	        IF SQLConnTables>0
	           SELECT SQLResult
	           INCnt=0
	           DO WHILE !EOF()
	              * Create a command to execute the stored procedure.
	              SQLCommand="sp_fkeys " + ALLTRIM(Table_Name)
	              * Execute the stored procedure and return data to a cursor.
	              =SQLEXEC(gnConnHandle,SQLCommand,'syskeys')
	              * Select the cursor.
	              SELECT SYSKeys
	              IF RECCOUNT()>0
	                 SELECT SQLKeys
	                 SQLKEY_Exists=.F.
	                 SCAN FOR Parent_Table_Name=SYSKeys.PKTable_Name ;
	                       AND Foreign_Table_Name=SYSKeys.FKTable_Name
	                    * Multicolumn key.
	                    * Concatenate to get the expression.
	                    REPLACE SQLKeys.Foreign_Column_Name WITH ;
	                       ALLTRIM(SQLKeys.Foreign_Column_Name) + ;
	                       "+"  + ALLTRIM(SYSKeys.FKColumn_Name)
	                    SQLKEY_Exists=.T.
	                 ENDSCAN
	                 IF !SQLKEY_Exists
	                    * Insert a new record into the SQLKeys cursor.
	                    INSERT INTO SQLKeys ;
	                       VALUES ;
	                       (SYSKeys.PKTable_Qualifier, SYSKeys.PKTable_Owner, ;
	                       SYSKeys.PKTable_Name, SYSKeys.PKColumn_Name, ;
	                       SYSKeys.FKTable_Qualifier, SYSKeys.FKTable_Owner, ;
	                       SYSKeys.FKTable_Name,SYSKeys.FKColumn_Name, ;
	                       SYSKeys.Key_Seq,SYSKeys.FK_NAME,SYSKeys.PK_Name)
	                 ENDIF
	              ENDIF
	              SELECT SQLResult
	              SKIP
	           ENDDO
	           =SQLDISCONN(gnConnHandle)
	        ENDIF
	     ENDIF
	     SELECT SQLKeys
	     BROW LAST
	     CLOSE ALL
	     RETURN
	
	In the Command window enter and run the following code:
	
	     DO SP_FKEYS
	
	REFERENCES
	==========
	
	Transact - SQL Help; search on: "sp_fkeys"
	
	(c) Microsoft Corporation 1998, All Rights Reserved. Contributions by John Desch,
	Microsoft Corporation.
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbClient KbClientServer kbDatabase kbSQL kbvfp kbvfp300b kbvfp500 kbvfp500a kbvfp600 kbMDAC250 kbSQLProg 
	Technology        : kbHWMAC kbOSMAC kbVFPsearch kbAudDeveloper kbMDACSearch kbMDAC250 kbVFP300bMac kbVFP300 kbVFP300b kbVFP500 kbVFP600 kbVFP500a
	Version           : MACINTOSH:3.0b; WINDOWS:2.5,3.0,3.0b,5.0,5.0a,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
