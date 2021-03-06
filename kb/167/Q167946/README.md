---
layout: page
title: "Q167946: FIX: ATL Service EXE Doesn't Build in Release Build"
permalink: /kb/167/Q167946/
---

## Q167946: FIX: ATL Service EXE Doesn't Build in Release Build

{% raw %}

	Article: Q167946
	Product(s): Microsoft C Compiler
	Version(s): winnt:5.0
	Operating System(s): 
	Keyword(s): kbVC500bug kbVC600fix
	Last Modified: 07-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, 32-bit Enterprise Edition, version 5.0 
	- Microsoft Visual C++, 32-bit Professional Edition, version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If you try to build a release mode of an ATL service EXE created with ATL COM
	AppWizard, you get the following the error message:
	
	  "error LNK2001: unresolved external symbol _main"
	
	CAUSE
	=====
	
	Builds in release mode automatically include the preprocessor directive
	_ATL_MIN_CRT, while the default ATL service code generated by the wizard
	requires the CRT library.
	
	RESOLUTION
	==========
	
	Remove _ATL_MIN_CRT from the list the preprocessor defines to allow CRT startup
	code to be included.
	
	1. From the Project menu, click Settings.
	
	2. In the Settings For drop-down list, select Multiple Configurations.
	
	3. In the Select project configuration(s) to modify dialog box that displays,
	  select the check boxes for all release versions, and then click OK.
	
	4. Click the C/C++ tab in the Project Settings dialog box, and then choose the
	  General category.
	
	5. Remove _ATL_MIN_CRT from the Preprocessor definitions edit box.
	
	NOTE: You can also remove calls to the CRT functions within the generated
	CServiceModule::LogEvent function.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This problem was corrected in Visual C++ version 6.0
	for Windows.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a Server EXE project using ATL COM Appwizard.
	
	2. Build one of the release builds.
	
	The error listed in the SYMPTOMS section should occur.
	
	REFERENCES
	==========
	
	For additional information about using CRT in ATL projects, please see the
	following article(s) in the Microsoft Knowledge Base:
	
	  Q165076 INFO: LNK2001 Error ATL Release Build
	
	Additional query words: kbserver kbvc500bug kbtool kbvc600fix kbwizard kberrmsg
	
	======================================================================
	Keywords          : kbVC500bug kbVC600fix 
	Technology        : kbVCsearch kbAudDeveloper kbVC500 kbVC32bitSearch kbVC500Search
	Version           : winnt:5.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
