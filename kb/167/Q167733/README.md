---
layout: page
title: "Q167733: PRB: Operator New Doesn't Throw bad_alloc Exception on Failure"
permalink: /kb/167/Q167733/
---

## Q167733: PRB: Operator New Doesn't Throw bad_alloc Exception on Failure

{% raw %}

	Article: Q167733
	Product(s): Microsoft C Compiler
	Version(s): 5.0,6.0
	Operating System(s): 
	Keyword(s): kbCompiler kbCPPonly kbCRT kbVC kbVC500 kbVC600
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The C Run-Time (CRT), used with:
	   - Microsoft Visual C++, 32-bit Enterprise Edition, versions 5.0, 6.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, versions 5.0, 6.0 
	   - Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	   - Microsoft Visual C++.NET (2002) 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Operator new does not throw a bad_alloc exception when it fails. It simply
	returns a null pointer.
	
	RESOLUTION
	==========
	
	Operator new does call the new handler function after it fails to procure the
	requestion block of memory, but before it returns the null pointer. An
	application could install a new handler to throw a bad_alloc exception as
	follows:
	
	     #include <new>
	     #include <new.h>
	     int my_new_handler(size_t) {
	        throw std::bad_alloc();
	        return 0;
	     }
	     int main () {
	        _PNH _old_new_handler;
	        _old_new_handler = _set_new_handler(my_new_handler);
	        /* ... application processing ... */ 
	        _set_new_handler(_old_new_handler);
	        return 0;
	     }
	
	To call new handler when malloc fails to obtain the requested block of memory,
	use the _set_new_mode function.
	
	To install the new handler before your global objects are initialized, create a
	class that sets the new handler in its constructor and installs the old new
	handler in its destructor. Create a global object of that type and use the
	init_seg pragma to force this global object to be initialized before any of your
	global objects. The example below demonstrates this. It also demonstrates the
	use of _set_new_mode to cause a failed malloc call to generate an exception.
	Note that to do this, the code below must reside in its own source file. You
	cannot change the initializations segment more than once per translation unit
	(source file) with the pragma init_seg.
	
	     #include <new>
	     #include <new.h>
	     #pragma init_seg(lib)
	     int my_new_handler(size_t) {
	     throw std::bad_alloc();
	     return 0;
	     }
	     struct my_new_handler_obj{
	     _PNH _old_new_handler;
	     int _old_new_mode;
	     _tag_g_new_handler_obj() {
	        _old_new_mode = _set_new_mode(1);
	        _old_new_handler = _set_new_handler(my_new_handler);
	     }
	     ~_tag_g_new_handler_obj() {
	        _set_new_handler(_old_new_handler);
	        _set_new_mode(_old_new_mode);
	     }
	
	     } _g_new_handler_obj;
	
	Operator new, as implemented by Visual C++ 5.0, ignores the function exception
	specification. So new(std::nothrow) still generates an exception if your new
	handler is installed to throw an exception as the examples above demonstrate. To
	change this behavior, override operator new as follows:
	
	     void *__cdecl operator new(size_t cb, const std::nothrow_t&) throw()
	     {
	      char *p;
	      try {
	          p = new char[cb];
	      }
	      catch (std::bad_alloc) {
	          p = 0;
	      }
	      return p;
	     }
	
	STATUS
	======
	
	This is a bug in Microsoft's implementation of operator new as this in not in
	conformance with the ANSI C++ Standard.
	
	REFERENCES
	==========
	
	For additional information, please see the following articles in the Visual C++
	5.0 online Help:
	
	  Using _set_new_handler
	
	  _set_new_handler
	
	  _set_new_mode
	
	  init_seg
	
	Additional query words:
	
	======================================================================
	Keywords          : kbCompiler kbCPPonly kbCRT kbVC kbVC500 kbVC600 
	Technology        : kbVCsearch kbAudDeveloper kbCRT
	Version           : :5.0,6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
