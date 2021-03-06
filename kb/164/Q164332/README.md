---
layout: page
title: "Q164332: WD97: Can't Use Spelling Checker If Text Uses Certain Fonts"
permalink: /kb/164/Q164332/
---

## Q164332: WD97: Can't Use Spelling Checker If Text Uses Certain Fonts

{% raw %}

	Article: Q164332
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:7.0,97
	Operating System(s): 
	Keyword(s): kbualink97 kbusage kbFontkbfaq
	Last Modified: 14-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	- Microsoft Word for Windows 95, version 7.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you run the spelling checker, Word may display the following message even
	if some of the words in your document are misspelled:
	
	  The spelling and grammar check is complete.
	
	This problem occurs if the text is formatted in a decorative or symbol font.
	
	CAUSE
	=====
	
	Word won't flag misspelled words if the text is formatted in a decorative or
	symbol font.
	
	The Word spelling checker skips text formatted with in any of the following
	fonts:
	
	- Arial CE
	
	- Arial Cyr
	
	- Arial Greek
	
	- Arial Narrow Special G1
	
	- Arial Special G1
	
	- Arial Special G2
	
	- Bookshelf Symbol 1
	
	- Bookshelf Symbol 2
	
	- Courier New CE
	
	- Courier New Cyr
	
	- Courier Greek
	
	- MS LineDraw
	
	- Times New Roman CE
	
	- Times New Roman Cyr
	
	- Times New Roman Greek
	
	- Times New Roman Special G1
	
	- Any Symbol Font such as: Marlett, Monotype Sorts, MS Outlook, Symbol,
	  Wingdings
	
	NOTE: There are other symbol fonts that are not listed here.
	
	
	MORE INFORMATION
	================
	
	To determine whether your font is a symbol font:
	
	1. On the Insert menu, click Symbol.
	
	2. Click the Symbols tab.
	
	3. Click the down arrow for the Font box.
	
	If the font you are using is displayed in this list here, it is considered a
	Symbol font and will not be checked for spelling errors in Word.
	
	For additional information, please see the following articles in the Microsoft
	Knowledge Base:
	
	  Q163059 WD97: Some Fonts Are Not Available in Word
	
	  Q159341 WD97: International Fonts Do Not Appear in Font List
	
	  Q89646 WD97: Error Msg: Text Formatted with No Proofing Was Skipped
	
	Additional query words: 97 8.0 word8 word97 certain
	
	======================================================================
	Keywords          : kbualink97 kbusage kbFont kbfaq
	Technology        : kbWordSearch kbWord97 kbWord97Search kbWord700Search kbZNotKeyword2 kbWord700
	Version           : WINDOWS:7.0,97
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
