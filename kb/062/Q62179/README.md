---
layout: page
title: "Q62179: NOGRAPH.OBJ Listed in Online Help Is Actually TXTONLY.OBJ"
permalink: /kb/062/Q62179/
---

## Q62179: NOGRAPH.OBJ Listed in Online Help Is Actually TXTONLY.OBJ

{% raw %}

	Article: Q62179
	Product(s): See article
	Version(s): 6.00
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | docerr | mspl13_c
	Last Modified: 26-NOV-1990
	
	In C version 6.00, an object file is sent out with the package to help
	decrease the size of executable files by about 8K to 10K. The online
	help states that the name of the object file is NOGRAPH.OBJ; in fact,
	the name of the file is TXTONLY.OBJ.
	
	To get any information on what this object file does, you can type "qh
	NOGRAPH.OBJ" (without the quotation marks). This will bring up
	QuickHelp with the information on this particular file.
	
	The help states that NOGRAPH.OBJ is used to reduce the size of an
	executable that uses only the text-mode functions from GRAPHICS.LIB.
	
	The actual filename is TXTONLY.OBJ.

{% endraw %}
