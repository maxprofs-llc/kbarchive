---
layout: page
title: "Q58035: Alternate Math (BC /FPa) Won't Always Produce Smaller .EXE's"
permalink: /kb/058/Q58035/
---

## Q58035: Alternate Math (BC /FPa) Won't Always Produce Smaller .EXE's

	Article: Q58035
	Product(s): See article
	Version(s): 6.00 6.00b 7.00 7.10 | 6.00 6.00b 7.00 7.10
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | docerr SR# S900122-49 | mspl13_basic
	Last Modified: 8-JAN-1991
	
	Using alternate math (BC /FPa) does not always produce smaller
	executable files than using the emulator math library (BC /FPi) when
	compiling with Microsoft BASIC Compiler Versions 6.00 and 6.00b for
	MS-DOS and MS OS/2 and Microsoft BASIC Professional Development System
	(PDS) Versions 7.00 and 7.10 for MS-DOS and MS OS/2.
	
	Page 8 of the "Microsoft BASIC Compiler 6.0: User's Guide" and Page
	562 of the "Microsoft BASIC 7.0: Programmer's Guide" (for 7.00 and
	7.10) misleadingly state that "it [the alternate math library] also
	creates a smaller executable file." Page 545 of the "Microsoft BASIC
	7.0: Programmer's Guide" misleadingly states that "alternate math is
	an IEEE-compatible math package optimized for speed and size."
	
	Although there is an initial space savings from using the alternate
	math libraries, each individual floating-point calculation can take
	more room using the alternate math library than the equivalent code
	for the emulator math library. This means that as the code grows in
	size, the initial space savings can be lost and the program can
	actually be larger using the alternate math package.
	
	Note: You will only notice a savings in the size of an executable
	compiled /FPa versus /FPi if the program is also compiled with the /O
	(stand-alone) option. If you compile as non stand alone with the
	alternate math library (/FPa) option, the program will actually
	contain both math libraries -- the compiled program will contain the
	alternate math routines, while the BASIC run-time module
	(BRUN60Ax.EXE, BRUN61Ax.EXE, or BRT70Axx.EXE) will contain the
	emulator math routines.
	
	The small program below demonstrates the size difference when
	compiling with and without the alternate math package.
	
	Compile the following program in these two ways:
	
	  BC /FPa test, test1.obj;
	  BC /FPi test, test2.obj;
	  LINK test1;
	  LINK test2;
	
	Code Example
	------------
	
	   REM  This is TEST.BAS
	   a = 6.1
	   b = 5.7
	   c = a * b
	
	The program compiled with the alternate math package (/FPa) produces
	larger code for the floating-point operation than the equivalent
	instructions using the emulator math library (/FPi). There is,
	however, an initial savings of about 4K when compiling with the
	alternate math library. In most programs, this initial savings offsets
	any extra code generated by floating-point calculation. In larger
	programs with lots of floating-point calculations, the extra code for
	each floating-point operation can actually create a larger executable
	file.