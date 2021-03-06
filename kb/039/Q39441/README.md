---
layout: page
title: "Q39441: The ORG Directive and Actual Offsets"
permalink: /kb/039/Q39441/
---

## Q39441: The ORG Directive and Actual Offsets

{% raw %}

	Article: Q39441
	Product(s): Microsoft Macro Assembler
	Version(s): 5.1,5.1a,6.0,6.0a,6.0b
	Operating System(s): 
	Keyword(s): 
	Last Modified: 06-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Macro Assembler (MASM), versions 5.1, 5.1a, 6.0, 6.0a, 6.0b 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The ORG directive in MASM does not necessarily produce an actual offset that
	matches the offset specified by "ORG XXX". For example, if you use "ORG 100h" in
	your program, the following code will not always begin at the 100h offset
	relative to the start of the segment.
	
	When you are using a .COM source file and there is only one module, the "ORG
	100h" will result in an actual offset of 100h for the code that follows the ORG
	statement. This behavior also occurs with segments with AT combine type (in
	which case segments are not combined by the linker, and no data or code is
	defined).
	
	However, if you have multiple modules and/or you are not dealing with a .COM
	source file, the "ORG 100h" produces an actual offset, which is somewhat greater
	than 100h.
	
	This behavior occurs because the linker, in these circumstances, will do some
	padding that you have no control over.
	
	MORE INFORMATION
	================
	
	In the following illustration (which deals with the source modules below), note
	that the ORG instruction increments the local offset by 100h, resulting in the
	offset of the PUSH instruction in example2 being 100h (that's what it would
	report in the listing file). However, when these modules are linked, all the
	portions of segment code are concatenated. Thus, EXAMPLE2.asm:code:100h is
	converted into code:113h. The order of concatenation is the order of linking.
	
	The following example illustrates the scenario:
	
	       Actual                      Offset
	       offset                      from start
	       from                        of segment
	       code                        code in module
	       -------                     ---------------
	               +-----------------+
	       0117    |   ret           | 0105
	       0116    |   pop           | 0103    test2.asm
	       0114    |   mov           | 0101
	       0113    |   push          | 0100
	       0013    |   org           | 0000
	               +-----------------+
	       0012    |   ret           | 0004
	       0011    |   pop           | 0003    test1.asm
	       000F    |   mov           | 0001
	       000E    |   push          | 0000
	               +-----------------+
	       000C    |   int           | 000C
	       0009    |   mov           | 0009    testmain.asm
	       0006    |   call          | 0006
	       0003    |   call          | 0003
	       0000    |   mov           | 0000
	               +-----------------+
	                   segment code
	
	  |---------------testmain.asm:       |---------------test1.asm:
	    code segment public 'code'           PUBLIC _test
	    assume cs:code                       code segment public 'code'
	                                         assume cs:code
	            mov     ax, 0a0ah            _test proc
	
	            extrn   _test:proc               push    bp
	            extrn   _test2:proc              mov     bp, sp
	
	            call    _test                    pop     bp
	            call    _test2                   ret
	
	            mov     ax, 4c00h            _test   ENDP
	            int     21h                  code ends
	            code ends
	
	            END                          END
	
	  |---------------test2.asm:
	     code segment public 'code'
	     assume cs:code
	             org     100h
	
	             PUBLIC  _test2
	     _test2    PROC
	
	             push    bp
	             mov     bp, sp
	
	             pop     bp
	             ret
	
	     _test2    ENDP
	     code ends
	             END
	
	Additional query words: kbinf 5.10 5.10a 6.00 6.00a 6.00b
	
	======================================================================
	Keywords          :  
	Technology        : kbMASMsearch kbAudDeveloper kbMASM510 kbMASM600 kbMASM600a kbMASM510a kbMASM600b
	Version           : :5.1,5.1a,6.0,6.0a,6.0b
	
	=============================================================================
	

{% endraw %}
