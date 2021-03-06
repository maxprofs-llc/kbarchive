---
layout: page
title: "Q66343: Uninitialized Globals in Wrong Segment in Assembly Listing"
permalink: /kb/066/Q66343/
---

## Q66343: Uninitialized Globals in Wrong Segment in Assembly Listing

{% raw %}

	Article: Q66343
	Product(s): See article
	Version(s): 6.00 6.00a | 6.00 6.00a
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | buglist6.00 buglist6.00a | mspl13_c
	Last Modified: 15-JAN-1991
	
	When declaring uninitialized global data, the segments allocated to
	store this data are the FAR_BSS segment for the compact, large, and
	huge memory models and the C_COMMON segment for the small and medium
	memory models. When the /Fa or /Fc compiler switches are used to
	produce assembly listings from the C source code, the listing that is
	generated actually has the segment incorrectly allocated as just _BSS.
	
	Using the /Fm switch to generate a map file from the linker will show
	that the segment is in fact FAR_BSS.
	
	Microsoft has confirmed this to be a problem in C version 6.00. We are
	researching this problem and will post new information here as it
	becomes available.

{% endraw %}
