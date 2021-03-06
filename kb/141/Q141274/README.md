---
layout: page
title: "Q141274: PRB: COleControl::Serialize Not Called with VB as Container"
permalink: /kb/141/Q141274/
---

## Q141274: PRB: COleControl::Serialize Not Called with VB as Container

{% raw %}

	Article: Q141274
	Product(s): Microsoft C Compiler
	Version(s): WINDOWS:4.0; winnt:2.0,2.1,2.2,4.0
	Operating System(s): 
	Keyword(s): kbActiveX kbCOMt kbCtrlCreate kbMFC kbPersistSt kbVBp400 kbVC200 kbVC400 kbGrpDSMFCATL
	Last Modified: 06-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Standard Edition for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 4.0 
	- The Microsoft Foundation Classes (MFC), used with:
	   - Microsoft Visual C++, 32-bit Editions, versions 2.0, 2.1, 2.2, 4.0 
	   - Microsoft OLE Control Developer's Kit (CDK) 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Although OLE controls are used with certain control containers (such as
	Microsoft Visual Basic version 4.0), the Serialize function for the control-
	derived class is not called. These containers allow the control to store its
	persistent information either by using the property sets or by using the
	IPersistPropertyBag interface. Both these methods call
	COleControl::DoPropExchange directly without calling the control's Serialize
	function.
	
	The resolution section of this article discusses a technique that you can use in
	the DoPropExchange method to store CObject-derived objects.
	
	CAUSE
	=====
	
	COleControl::Serialize is called by the framework when an OLE control container
	uses one of the following persistent storage interfaces for loading and saving
	the control: IPersistStorage, IPersistStreamInit, or IPersistMemory.
	
	If a control container uses any other method to store the control's persistent
	information, then Serialize for the control-derived class will not be called.
	Microsoft Visual Basic, for example, uses either IPersistPropertyBag or property
	sets to store the persistent information for an OLE control; therefore, the
	Serialize function for a control is not called when Visual Basic is used as the
	control container.
	
	RESOLUTION
	==========
	
	Although there is no direct support for serializing CObject-derived objects in
	COleControl::DoPropExchange, you might want to use the following technique to
	store objects in an OLE control:
	
	1. Allocate a block of memory with GlobalAlloc.
	
	     // cbGuess is a guess of how much memory will be needed.
	     // If more is needed, CSharedFile will reallocate.
	     HGLOBAL hMem = GlobalAlloc(GPTR, cbGuess);
	     BYTE *pbMem = (BYTE *)hMem;
	
	2. Construct an instance of CSharedFile and attach it to the memory block,
	  starting four bytes in. Because the CSharedFile class is not yet documented,
	  include afxpriv.h:
	
	     CSharedFile file;
	     file.Attach(pMem + sizeof(DWORD), cbGuess - sizeof(DWORD));
	
	3. Construct an instance of CArchive on the file:
	
	     CArchive ar(&file, CArchive::store);
	
	4. Write the CObject-derived objects into the archive:
	
	     // store data in the archive
	     // for example, if m_myObject is a CObject-derived object, then
	     m_myObject.Serialize(ar);
	
	5. Get the length of the file and write it into the first DWORD of the memory
	  block:
	
	     *(DWORD*)pbMem = file.GetLength();
	
	6. Pass the memory block to PX_Blob:
	
	     PX_Blob(pPX, _T("MyObjects"), hMem);
	
	This code could be used for loading the objects back out of the blob. For more
	information about how to use PX_Blob to serialize/de-serialize data, Please see
	the following article in the Microsoft Knowledge Base:
	
	  Q137333 DOCERR: How to Use the PX_Blob Function
	
	To get optimal performance in IPersistStreamInit, ensure that the OLE control
	maintains a separate Serialize method that writes the CObjects directly to its
	archive. Care should be taken to save all of the control's persistent data in
	both Serialize and DoPropExchange.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	An OLE control generated using ControlWizard can read and write its persistent
	state using one of the following interfaces: IPersistMemory, IPersistStorage,
	IPersistStreamInit, IPersistPropertyBag (not implemented in versions before
	Visual C++ 4.x), and IDataObject through the property sets implementation. Each
	of these interfaces with the exception of IPersistPropertyBag and IDataObject
	call COleControl::Serialize passing in a CArchive. This archive could be used to
	store CObject-derived objects as part of the control's persistence.
	
	Some OLE control containers (like Microsoft Visual Basic) use the "save as text"
	mechanism in order to allow as much of the OLE control's state to be represented
	in a human-readable format. For optimizing this mechanism, the interfaces
	IPropertyBag and IPersistPropertyBag are used and therefore are recommended for
	containers like Visual Basic. IPropertyBag is implemented by the container and
	is roughly analogous to IStream. IPersistPropertyBag is implemented by controls
	and is roughly analogous to IPersistStream(Init).
	
	Visual Basic uses the control's IPersistPropertyBag interface, if one is
	implemented by the control, or it uses the property sets. Property sets are
	communicated from and to the control through IDataObject::GetData and
	IDataObject::SetData, implemented by the control. Note that OLE controls
	generated using earlier versions of Visual C++ don't provide an implementation
	for IPersistPropertyBag.
	
	The implementation provided by the MFC framework for IPersistPropertyBag and
	property sets directly call COleControl::DoPropExchange passing in an instance
	of either CPropbagPropExchange or CPropsetPropExchange respectively.
	
	REFERENCES
	==========
	
	OLE Controls Inside Out - by Adam Denning
	
	Additional query words: 2.00 2.10 2.20 3.00 3.10 3.20 4.00
	
	======================================================================
	Keywords          : kbActiveX kbCOMt kbCtrlCreate kbMFC kbPersistSt kbVBp400 kbVC200 kbVC400 kbGrpDSMFCATL 
	Technology        : kbVBSearch kbAudDeveloper kbPTNotAssigned kbMFC kbZNotKeyword2
	Version           : WINDOWS:4.0; winnt:2.0,2.1,2.2,4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
