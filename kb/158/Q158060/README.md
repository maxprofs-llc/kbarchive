---
layout: page
title: "Q158060: WD97: VBA Code Lost After Converting to Another Document Format"
permalink: /kb/158/Q158060/
---

## Q158060: WD97: VBA Code Lost After Converting to Another Document Format

{% raw %}

	Article: Q158060
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97; :Service Release 1 (SR-1)
	Operating System(s): 
	Keyword(s): kberrmsg kbother kbdta kbconversion kbdtacode word97
	Last Modified: 14-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	- Microsoft Word 97 for Windows, version Service Release 1 (SR-1) 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you save a Word 97 document that contains Visual Basic code in another
	document format, such as Rich-Text Format (RTF), the Visual Basic code is lost.
	
	NOTE: In the version of Microsoft Word 97 prior to Service Release 1 (SR-1), Word
	does not display a warning dialog box that macros will be lost when you save to
	another document format.
	
	In Microsoft Word 97 Service Release 1 (SR-1), a warning appears as follows:
	
	  All macros in this document will be lost if the document is saved in
	  <Selected Document Format>. Do you want to save in this format anyway?
	
	
	CAUSE
	=====
	
	None of the converters that ship with Word 97 supports the conversion of Visual
	Basic code. If you need to save a document in a format other than Word 97, make
	sure you have a backup copy of your Word 97 document before you convert it.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Word 97 for Windows.
	
	REFERENCES
	==========
	
	For more information about getting help with Microsoft Visual Basic for
	Applications, please see the following article in the Microsoft Knowledge Base:
	
	  Q163435 VBA: Programming Resources for Visual Basic for Applications
	
	Additional query words: conversion converting textconv translation translating translated converted converts translates vb vba vbe script coding programming rich text lost missing gone disappears disappeared empty
	
	======================================================================
	Keywords          : kberrmsg kbother kbdta kbconversion kbdtacode word97 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2 kbWord97SR1
	Version           : WINDOWS:97; :Service Release 1 (SR-1)
	Issue type        : kbprb
	Solution Type     : kbnofix
	
	=============================================================================
	

{% endraw %}
