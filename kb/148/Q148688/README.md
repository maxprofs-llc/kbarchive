---
layout: page
title: "Q148688: FIX: C2243 on Friend Overload o"
permalink: /kb/148/Q148688/
---

## Q148688: FIX: C2243 on Friend Overload o

{% raw %}

	Article: Q148688
	Product(s): Microsoft C Compiler
	Version(s): 4.0 4.1 4.2
	Operating System(s): 
	Keyword(s): kbCompiler kbCPPonly kbLangCPP kbVC kbVC500fix
	Last Modified: 03-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The C/C++ Compiler (CL.EXE), included with:
	   - Microsoft Visual C++, 32-bit Editions, versions 4.0, 4.1 
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 4.2 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 4.2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The following error is generated:
	
	  
	
	  error C2243: 'abstract declarator' : conversion from 'class Derived *'
	  to 'const class Base<Type> &' exists, but is inaccessible
	
	in code that contains all of the following:
	
	- A template base class that has a friend function that overloads operator
	  << for ostream.
	
	- A derived class that privately inherits its base class and has a friend
	  function that overloads operator << for ostream where the second
	  argument to the operator << is a reference to const type (const Derived
	  &).
	
	- A call to the operator << passing a non-const derived type object.
	
	RESOLUTION
	==========
	
	Use one of the following two workarounds to resolve the problem:
	
	- Typecast the derived object to a reference to const type when using the
	  operator <<.
	
	-or-
	
	- Make the base class public instead of private.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug was corrected in Visual C++ version 5.0.
	
	MORE INFORMATION
	================
	
	Sample Code
	-----------
	
	     /* Compile options needed: None
	     */ 
	     #include <iostream.h>
	     template<class T>
	     class Base;
	     template<class T>
	     ostream& operator<<(ostream& s, const Base<T> & a)
	     {
	        return s;
	     }
	     template<class T>
	     class Base
	     {
	     public:
	        friend ostream& operator<<(ostream& s, const Base<T>& a);
	     };
	     class Derived;
	     ostream& operator<<(ostream& s, const Derived& a)
	     {
	        return s;
	     }
	     // Replace 'private' by 'public' in the following line
	     // to avoid the error (work around # 2)
	     class Derived : private Base<char> {
	     public:
	        friend ostream& operator<<(ostream& s, const Derived& a);
	     };
	     void main(void)
	     {
	        Derived objDerived;
	        // The C2243 error is generated for the following line.
	        // Uncomment the typecast to avoid the error (work around # 1)
	        cout << /*(const Derived&)*/ objDerived;
	     }
	
	Additional query words: kbVC400bug
	
	======================================================================
	Keywords          : kbCompiler kbCPPonly kbLangCPP kbVC kbVC500fix 
	Technology        : kbVCsearch kbAudDeveloper kbCVCComp
	Version           : 4.0 4.1 4.2
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
