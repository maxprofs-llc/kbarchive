---
layout: page
title: "Q31495: Macro to Enter Form Feed or Control Characters in Editor"
permalink: /kb/031/Q31495/
---

## Q31495: Macro to Enter Form Feed or Control Characters in Editor

{% raw %}

	Article: Q31495
	Product(s): See article
	Version(s): 1.00 | 1.00
	Operating System(s): DOS | OS/2
	Keyword(s): ENDUSER | tar62237 | mspl13_basic
	Last Modified: 1-NOV-1988
	
	The form-feed characters and control characters below can be entered
	in a file being edited by the Microsoft Editor.
	
	The following macro inserts a linefeed, (CTRL+L), and a newline, and
	binds it to the F6 key. To enter a CTRL+L, use the Graphic assignment
	on Page 48 of the "Microsoft Editor User's Guide" when editing your
	TOOLS.INI file:
	
	graphic:ctrl+l
	
	FFM:="L" newline   ; Instead of the L shown here, insert a CTRL+L
	FFM:F6             ; with the quote function "CTRL+P CTRL+L"
	
	The macro below allows you to enter control key values. The
	following line binds "quote" to F5. Quote allows you to enter any key
	as input (i.e., control key values, etc). This means if you type "F5"
	followed by a "CTRL+X", you will see a "\030" instead of "arg":
	
	quote:F5.

{% endraw %}
