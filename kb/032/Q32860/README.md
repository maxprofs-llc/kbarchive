---
layout: page
title: "Q32860: Using /LA and .FARDATA? Generates Incorrect Listing File"
permalink: /kb/032/Q32860/
---

## Q32860: Using /LA and .FARDATA? Generates Incorrect Listing File

{% raw %}

	Article: Q32860
	Product(s): See article
	Version(s): 5.10   | 5.10
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | buglist5.10 | mspl13_masm
	Last Modified: 19-JUL-1988
	
	The MASM command-line option /LA will show all code generated by
	the high-level-language features. When the .FARDATA? directive is
	used, the code generated in the listing file places the "@CurSeg ends"
	statement in the wrong place.
	   Microsoft has confirmed this to be a problem in Version 5.10. We
	are researching this problem and will post new information as it
	becomes available.
	
	   The following is an assembler source and listing file:
	
	    .model small
	    .fardata?
	    .data
	    end
	
	    .model small
	    assume cs:@code,ds:@data,ss:@data
	    .fardata?
	    FAR_BSS segment 'FAR_BSS'
	    .data
	    _DATA segment 'DATA'
	    @CurSeg ends
	    end
	    @CurSeg ends
	
	    first "@CurSeg ends" statement should be place before the _DATA
	segment is declared.

{% endraw %}
