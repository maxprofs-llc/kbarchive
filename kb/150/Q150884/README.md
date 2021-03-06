---
layout: page
title: "Q150884: FIX: C1001 Fatal Error in File Main.c, Line 413 for /O1 or /O2"
permalink: /kb/150/Q150884/
---

## Q150884: FIX: C1001 Fatal Error in File Main.c, Line 413 for /O1 or /O2

{% raw %}

	Article: Q150884
	Product(s): Microsoft C Compiler
	Version(s): 4.00 4.10
	Operating System(s): 
	Keyword(s): kbCompiler kbCPPonly kbVC
	Last Modified: 30-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The C/C++ Compiler (CL.EXE), included with:
	   - Microsoft Visual C++, 32-bit Editions, versions 4.0, 4.1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Using /O1 (minimize size) or /O2 (maximize speed) causes a C1001 error in a try
	block with the following error message:
	
	  
	
	  fatal error C1001: INTERNAL COMPILER ERROR
	   (compiler file '\school.tp3\test\c10\src\P2\main.c', line 413)
	
	Additionally, C++ exception handling must be enabled (/GX). If the warning level
	is set to 4 (/W4), C4702 (unreachable code) warnings are issued before the C1001
	fatal error.
	
	CAUSE
	=====
	
	The cause of the problem is having both /Og (global optimizations) and inline
	function expansion /Ob1 (Only __inline) or /Ob2 (Any Suitable) compiling. /O1
	and /O2 are both compound switches, including /Og and /Ob1.
	
	RESOLUTION
	==========
	
	Disable either global optimizations (/Og-) or inline function expansion (/Ob1-
	or /Ob2-). Please see the More Information section below.
	
	STATUS
	======
	
	Microsoft has confirmed this to be bug in the Microsoft products listed at the
	beginning of this article. This bug was corrected in Visual C++ 32-bit Edition
	version 4.2.
	
	MORE INFORMATION
	================
	
	The following code reproduces the error when compiled:
	
	     // Compile option needed are: /GX, /W4, and /O1(minimize size)
	     // or /O2 (maximize speed)
	     struct A
	     {
	             ~A(){}
	     };
	     struct B
	     {
	             A       a;
	     };
	     void main(void)
	     {
	             try                     // line 17
	             {
	                 B       *pB = new B[4];
	                 delete [] pB;  // line 20, warning C4702: unreachable code
	             }
	             catch(...)
	             {
	             }
	     }
	
	The following error message is generated:
	
	  
	
	  test.cpp(17) : fatal error C1001: INTERNAL COMPILER ERROR
	    (compiler file '\school.tp3\test\c10\src\P2\main.c', line 413)
	
	Compiling from command line with both /Og (global optimizations) and in-line
	function expansion, /Ob1(Only __inline) or /Ob2 (Any Suitable), reproduces the
	error. For instance, using:
	
	  cl  /Og /Ob1 /GX /W4 test.cpp
	
	Compiling with the following switch settings in command line does not produce
	errors:
	
	  cl  /Og /GX /W4 test.cpp
	
	- or -
	
	  cl  /Ob1 /GX /W4 test.cpp
	
	One workaround when using /O1 or /O2 in Developer Studio is to disable In-line
	function expansion (Build:Settings, C++ Tab, Optimizations category). Another
	workaround is to disable global optimizations. To accomplish this, choose Custom
	for the type of optimization (Build:Settings, C++ Tab, Optimizations category).
	Check all categories that apply, but do not check global optimizations. This
	behavior is similar to using the components of /O1 or /O2 and eliminating /Og).
	An additional method is to leave /O1 or /O2 intact and manually add /Og- to the
	Project Options.
	
	Additional query words: kbVC400bug 4.00 4.10 4.20 vcfixlist420 CPPIss
	
	======================================================================
	Keywords          : kbCompiler kbCPPonly kbVC 
	Technology        : kbVCsearch kbAudDeveloper kbCVCComp
	Version           : 4.00 4.10
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
