---
layout: page
title: "Q43601: CodeView May Single Step onto a Comment Line"
permalink: /kb/043/Q43601/
---

## Q43601: CodeView May Single Step onto a Comment Line

{% raw %}

	Article: Q43601
	Product(s): See article
	Version(s): 2.20   | 2.20
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | buglist2.20 | mspl13_basic
	Last Modified: 2-JUN-1989
	
	When using CodeView to single step the following program, the current
	execution line will be put on the first comment line. CodeView should
	always skip over the comment line.
	
	The program is compiled as required for running in CodeView. The
	compiling command used could be the following:
	
	   cl /Zi /Od test.c
	
	Microsoft has confirmed this to be a problem with CodeView Version
	2.20. We are researching the problem and will post new information as
	it becomes available.
	
	This problem has no effect on the application program's performance.
	
	The following is the program:
	
	/*   test.c   */
	#include <stdio.h>
	int i = 1 ;
	void main (void)
	{
	if ( i )
	     i = 0 ;
	     /* first comment line */
	else
	     /* more comment */
	     i = 1 ;
	}

{% endraw %}
