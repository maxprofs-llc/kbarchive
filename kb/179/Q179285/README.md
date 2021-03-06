---
layout: page
title: "Q179285: PRB: Disabled Developer Studio Add-Ins Not Unloaded From Memory"
permalink: /kb/179/Q179285/
---

## Q179285: PRB: Disabled Developer Studio Add-Ins Not Unloaded From Memory

{% raw %}

	Article: Q179285
	Product(s): Microsoft C Compiler
	Version(s): 
	Operating System(s): 
	Keyword(s): kbVC500 kbVC600
	Last Modified: 17-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, 32-bit Enterprise Edition, versions 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When a DLL add-in is disabled in Developer Studio through the Tools/Customize
	dialog box (click Customize on the Tools menu), the DLL is not unloaded from
	memory. As a result, if the add-in is being built in Developer Studio, the
	linker cannot overwrite the still-loaded DLL and will give the following error
	message:
	
	  LINK : fatal error LNK1168: cannot open Debug/test.dll for writing
	
	NOTE: Test.dll is the name of the add-in DLL.
	
	RESOLUTION
	==========
	
	After disabling the add-in, close Developer Studio then reopen Developer Studio.
	The development environment will not load the add-in, and therefore changes may
	be made to the DLL.
	
	STATUS
	======
	
	This behavior is by design.
	
	REFERENCES
	==========
	
	The online help topic "Disconnecting Add-ins from Developer Studio" describes
	part of the process of disabling an add-in:
	
	  If you remove the check mark from an add-in, you will unload it. When you
	  unload it, the add-in loses all of its toolbar and keystroke assignments.
	
	This statement is misleading because the add-in is not unloaded from memory, but
	rather the functions provided in the add-in are unloaded from Developer Studio.
	This is made clearer in the topic "How Add-ins Connect and Disconnect":
	
	  When Developer Studio quits, it unloads each add-in by calling the
	  OnDisconnection method exposed by the add-in's DSAddIn object.
	
	Consult your product documentation for more information on creating and using
	add-ins in Developer Studio.
	
	Additional query words: VSDSAuto VwbIss kbvc600 kbvc500 kbDSSTools kbdse kbDSupport
	
	======================================================================
	Keywords          : kbVC500 kbVC600 
	Technology        : kbVCsearch kbAudDeveloper kbVC500 kbVC600 kbVC32bitSearch kbVC500Search
	Issue type        : kbprb
	Solution Type     : kbnofix
	
	=============================================================================
	

{% endraw %}
