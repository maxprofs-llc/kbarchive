---
layout: page
title: "Q182110: IIS Access Violates Calling Local COM Server"
permalink: /kb/182/Q182110/
---

## Q182110: IIS Access Violates Calling Local COM Server

{% raw %}

	Article: Q182110
	Product(s): Internet Information Server
	Version(s): WINNT:3.0,4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 20-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Internet Information Server versions 3.0, 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Internet Information Server (IIS) may access violate when using an in- process
	COM object to expose methods for a local COM server that is running as a
	service. The access violation is more likely to occur on multi- processor
	servers that are extremely busy. The access violation will occur in seemingly
	unrelated areas because the problem affects several areas of the COM support
	code.
	
	The debug stack will look similar to the following example:
	
	  Example Stack:
	  DbgBreakPoint
	  RtlpBreakPointHeap
	  RtlpValidateHeapEntry
	  RtlDebugSizeHeap
	  RtlSizeHeap
	  CRetailMalloc_GetSize
	  MemSize(void * 0xfeeefeee)
	  MemFree(void * 0xfeeefeee)
	  CTypeLib2::~CTypeLib2() line 56 + 15 bytes
	  CTypeLib2::`scalar deleting destructor'() + 20 bytes
	  CTypeLib2::Release(CTypeLib2 * const 0x0344e428)
	  CTypeInfo2::Release(CTypeInfo2 * const 0x0344eac8)
	  CreateRealProxy
	  CProxyWrapper::Connect
	  ConnectIPIDEntry@CStdMarsha
	  MakeCliIPIDEntry@CStdMarshal
	  UnmarshalIPID@CStdMarshal
	  RemQIAndUnmarshal@CStdMarshal
	  QueryRemoteInterfaces@CStdMarshal
	  QueryMultipleInterfaces@CInternalUnk
	  QueryInterface@CInternalUnk@CStdIdentity
	  CreateInstance
	  CreateInstance
	  ::FinalConstruct()
	
	CAUSE
	=====
	
	The ref count for a contained local servers Type Library can be incorrectly set
	when the OLE automation code is set to multithreading. As a result, the Type
	Library is released too soon.
	
	The access violation occurs when the in-process object creates or references
	methods in the local server after the Type Library has been released.
	
	This problem only occurs when the multiprocessor IIS computer is under stress and
	the time frame of the ref counter is incorrectly set too small.
	
	RESOLUTION
	==========
	
	A supported fix that corrects this problem is now available from Microsoft, but
	has not been fully regression tested and should be applied only to systems
	experiencing this specific problem. If you are not severely affected by this
	specific problem, Microsoft recommends that you wait for the next service pack.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information on support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT version 4.0.
	
	MORE INFORMATION
	================
	
	A fix was made to the Oleaut32.dll file to add additional thread synchronization
	so that the ref counter is protected when it is under stress.
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbiisSearch kbiis400 kbiis300
	Version           : WINNT:3.0,4.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
