---
layout: page
title: "Q61305: Warning C4018: signed/unsigned Mismatch Not in QuickHelp"
permalink: /kb/061/Q61305/
---

## Q61305: Warning C4018: signed/unsigned Mismatch Not in QuickHelp

{% raw %}

	Article: Q61305
	Product(s): See article
	Version(s): 6.00   | 6.00
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | docerr | mspl13_c
	Last Modified: 23-JAN-1991
	
	Compiler warning C4018 is not documented in the online help files that
	come with the Microsoft C version 6.00 compiler. C4018 is a warning
	message that is new to C 6.00, and it is generated at warning level 3
	or 4 when the compiler finds code comparing a signed and an unsigned
	data type.
	
	Code Example
	------------
	
	The following code generates C4018 at warning level 3 or 4:
	
	unsigned int u = 2;
	int i = 1;
	
	void main ( void )
	{
	    if ( i == u )    // Warning is generated on this line.
	        i = 0;
	}

{% endraw %}
