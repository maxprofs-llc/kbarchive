---
layout: page
title: "Q34410: Far Pointer Comparisons Don't Account for Aliases"
permalink: /kb/034/Q34410/
---

## Q34410: Far Pointer Comparisons Don't Account for Aliases

{% raw %}

	Article: Q34410
	Product(s): See article
	Version(s): 5.10   | 5.10
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | | mspl13_c
	Last Modified: 12-OCT-1988
	
	The code generated to compare two far pointers for equality does not
	account for the possibility of the pointers having different segments
	and offsets, yet still pointing to the same location.
	
	This is correct behavior for the compiler. Only huge pointers are
	normalized. Near and Far pointers that point into the same segment are
	assumed to have the same segment values; any differences between them
	must be in the offset.
	
	Normalizing pointers would involve a tremendous performance penalty
	under MS-DOS and would be impossible under OS/2 due to the
	protected-mode addressing scheme.

{% endraw %}
