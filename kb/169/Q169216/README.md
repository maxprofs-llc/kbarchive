---
layout: page
title: "Q169216: Using Winscl.exe to Remove Corrupted WINS Entries by Version ID"
permalink: /kb/169/Q169216/
---

## Q169216: Using Winscl.exe to Remove Corrupted WINS Entries by Version ID

{% raw %}

	Article: Q169216
	Product(s): Microsoft Windows NT
	Version(s): WinNT:3.51,4.0
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	You can use the Winsdmp.exe and Winscl.exe Resource Kit utilities to remove
	corrupt entries from the Windows Internet Name Service (WINS) database.
	
	This article explains how to use Winsdmp.exe to determine the version ID of the
	corrupt entries and how to use Winscl.exe to remove those entries.
	
	In certain cases (such as when names contain extended characters or spaces) it is
	necessary to remove entries based on their version ID, rather than name (using
	the DN option). The DN option fails when you attempt to remove these entries
	with extended characters or spaces. Also, the DN option only removes single
	entries, and does not remove ranges of entries.
	
	NOTE: The WINS Server must be running when you use Winscl.exe to modify the WINS
	database.
	
	MORE INFORMATION
	================
	
	1. Run Winsdmp.exe to dump the WINS database.
	
	  Example:
	
	  WINSDMP 130.0.10.1 > Winsdata.txt
	
	  The following is an example line that information that WINSDMP provides:
	
	  130.10.10.10,"TEST           ",0,17,3,0,0,502,0,820870950,1,130.0.25.14
	
	  The following table lists each item in the example above on the left side and
	  the corresponding explanation for the example item on the right side:
	
	     Example Item        Explanation for Example Item
	     ------------        ----------------------------
	     130.10.10.10        The IP address of the owner of the entry
	     "TEST"              The NetBIOS name of the entry
	     0                   The 16th character of the NetBIOS name
	     17                  The number of characters in the name
	                         (15 for NetBIOS name + 2 for ID)
	     3                   Type of Record
	     0                   State of Record
	     0                   Version ID (High order)
	     502                 Version ID (Low order)
	     0                   Static Flag
	     820870950           Time Stamp
	     1                   Number of records in entry
	     130.0.25.14         IP Addresses assigned to entry
	
	  The possible Record Type values are defined as:
	
	     UNIQUE        = 0
	     NORMAL GROUP  = 1
	     SPECIAL GROUP = 2
	     MULTIHOMED    = 3
	
	  The possible Record State values are defined as:
	
	     ACTIVE    = 0
	     RELEASED  = 1
	     TOMBSTONE = 2
	
	2. Use the data from the dump to compile a list of entries (or a range of
	  entries) to be removed from the WINS database. Then use the Winscl.exe
	  utility to delete the individual entry or the range of entries.
	
	If you want to remove a range of consecutive entries, enter the minimum and
	maximum versions when prompted by WINSCL. If you want to remove multiple
	non-consecutive entries, they must be processed individually.
	
	The example below uses low order bit of the version ID (which is 502 in the
	earlier example) and the high order bit (which is 0 in the earlier example) to
	remove a single WINS entry.
	
	Example: (with annotations in <<< >>>)
	
	Winscl.exe
	TCP/IP or named pipe. Enter 1 for TCP/IP - 1 <<<enter 1
	here>>>
	Address of Nameserver to contact--130.0.10.1 <<<this is the IP address
	of the WINS server>>>
	RN-Register a name
	QN-Query a name
	DN-Delete a name
	GV-Get the current vers. counter value
	GM-Get the Owner Id to Max. Vers. No. mappings
	GMO-Get the Owner Id to Max. Vers. No. mappings (3.5 WINS)
	GST-Get WINS statistics
	GSTO-Get WINS statistics (3.5 WINS)
	PUSHT-Send a push trigger to another WINS
	PULLT-Send a pull trigger to another WINS
	SI-Statically initialize the WINS
	CC-Initiate consistency check on the WINS - HIGH OVERHEAD OPERATION
	SC-Initiate scavenging on the WINS
	DRR-Delete all or a range of records
	PRR-Pull all or a range of records from another WINS
	GRBN-Get records by name
	GRBV-Get Records by version numbers
	BK-Backup the database
	RS-Restore the db
	RSO-Restore the db (created by a pre-SUR WINS)
	RC-Reset WINS counters
	CR-Count the number of recs. in the db
	GI-Get Info about WINS
	SDB-Search the db
	GD-Get domain names
	DW-Delete WINS records and info.
	CW-Connect Wins
	WA-Get Add of current Wins
	ME-SHOW MENU
	NOME-DONT SHOW MENU
	EX-Terminate winscl
	Command - DRR <<<this command deletes a record or range of
	records>>>
	Address of Owner Wins -- 130.10.10.10 <<<this is the IP address of the
	WINS server which owns the entry>>>
	Min. Vers. No (<high part> <low part> -- 0 502 <<<this is
	the minimum version ID>>>
	Max. Vers. No (<high part> <low part> -- 0 502 <<<this is
	the maximum version ID. In this case, since the min. and max. are the same, only
	one registration will be deleted>>>
	Status returned is (SUCCESS - 0)
	
	NOTE: If the Maximum Version Number is different than the Minimum Version Number
	it will delete the full range. The version number can also be obtained from the
	WINS Manager in the Show Database window under version ID column. The version ID
	shown in this window is in HEX. It needs to be converted to decimal to use with
	Winscl.exe. For example, if the version ID is 201 for the record that needs to
	be deleted, the Minimum version number becomes 0 513 when used with WINSCL.
	
	For more information on using WINSCL.EXE, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q137582 Using WINSCL.EXE
	
	Additional query words: bit doublewide order
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbWinNTsearch kbWinNT351search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS351search
	Version           : WinNT:3.51,4.0
	
	=============================================================================
	

{% endraw %}
