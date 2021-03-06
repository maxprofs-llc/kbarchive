---
layout: page
title: "Q113098: Bookshelf: Can't Run Reinstall from a Different Drive"
permalink: /kb/113/Q113098/
---

## Q113098: Bookshelf: Can't Run Reinstall from a Different Drive

{% raw %}

	Article: Q113098
	Product(s): Microsoft Home Multimedia Titles
	Version(s): 1994 edition,1995 edition
	Operating System(s): 
	Keyword(s): 
	Last Modified: 09-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Bookshelf for Windows versions 1994 edition, 1995 edition 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If you try to run Bookshelf Setup in maintenance mode from a different drive
	than the one you originally used when you installed the program, you may receive
	an error message similar to the following:
	
	  Setup Message
	  Could not open the file named X:\MSSTP\BOOKS94.STF.
	  Abort, Retry, or Ignore?
	
	where X is the letter of the hard drive where you installed the program.
	
	RESOLUTION
	==========
	
	To work around this problem, do one of the following:
	
	- Delete the Bs94.ini or Bshelf95.ini file from the Windows directory.
	
	  -or-
	
	- Open the .ini file in Notepad and edit the drive= line in the [Options]
	  section to point to the drive you now want to use to reinstall Bookshelf.
	  Save the file.
	
	MORE INFORMATION
	================
	
	This problem occurs if you run the Setup program in maintenance mode and then
	choose the Reinstall button. By design, the Reinstall option runs the original
	installation again, using all the same options you originally selected. By
	default, it chooses the original drive as well.
	
	Use a text editor, such as Microsoft Notepad, to make the changes to the Bs94.ini
	or Bshelf95.ini file, which is located in the Windows folder. For example, if
	you now want to reinstall from drive e:, edit the [Options] line to read as
	follows:
	
	  [Options]
	  drive=E:\
	
	After either deleting or editing and saving the .ini file, run Setup again and
	choose Reinstall. It should now work correctly.
	
	For more information about how to edit files in Windows, see your Windows printed
	documentation or online Help.
	
	Additional query words: msn_bookshelf 1994 multi media multimedia multi- acmsetup acmsetup.exe 1995
	
	======================================================================
	Keywords          :  
	Technology        : kbHomeMMsearch kbBookshelfSearch kbBookShelf1994 kbBookShelf1995
	Version           : :1994 edition,1995 edition
	
	=============================================================================
	

{% endraw %}
