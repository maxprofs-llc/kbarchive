---
layout: page
title: "Q157073: PRB: Exception Not Caught Using CArchive or CFile"
permalink: /kb/157/Q157073/
---

## Q157073: PRB: Exception Not Caught Using CArchive or CFile

{% raw %}

	Article: Q157073
	Product(s): Microsoft C Compiler
	Version(s): winnt:2.0,2.1,2.2,4.0,4.1,4.2
	Operating System(s): 
	Keyword(s): kbFileIO kbMFC kbVC200 kbVC400 kbVC420 kbGrpDSMFCATL kbExceptHandCPP kbExceptHandling
	Last Modified: 04-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), used with:
	   - Microsoft Visual C++, 32-bit Editions, versions 2.0, 2.1, 2.2, 4.0, 4.1 
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 4.2 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 4.2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When using CArchive or CFile, Visual C++ exceptions may not be caught if the
	CArchive and/or CFile are in the same try block as a read or write:
	
	     void Test1()
	     {
	          try {
	             //Drive A: should contain a floppy with zero bytes free
	             CFile file("A:\\BadFile.tmp", CFile::modeCreate
	                        | CFile::shareExclusive | CFile::modeWrite );
	             try {
	                 CArchive archive(&file, CArchive::store);
	                 //Fill up disk, and cause a
	                 //CFileException::diskFull exception
	                 while(1)
	                     archive << (DWORD)17;
	             }
	             catch ( CFileException* ex ) {
	                 ex->Delete();
	             }
	             catch (...) {
	                 ASSERT(FALSE);
	             }
	         }
	         catch ( CFileException* ex ) {
	             ex->Delete();
	         }
	         catch (...){
	             ASSERT(FALSE);
	         }
	     }
	
	In this case, if the disk is full, the exception is not caught, terminate() is
	called, and the application exits.
	
	CAUSE
	=====
	
	In the process of handling exceptions, objects inside the try block are
	destructed before the first catch block. During unwinding, when a second
	exception is thrown by a destructor before the first exception is caught,
	terminate() is called.
	
	Both the destructors for CArchive and CFile attempt to flush the buffer and close
	the open file. This can cause a second exception to get thrown and terminate()
	to get called.
	
	RESOLUTION
	==========
	
	Make sure that the CArchive or CFile object is not inside the same try block as
	any read or write on that object.
	
	The CArchive object should also not be inside of the same try block as the CFile
	object it uses unless the CArchive was created in the CArchive::bNoFlushOnDelete
	mode. If this mode is used, the CArchive and CFile can safely be in the same try
	block. Care must be taken to call CArchive::Flush() before the CArchive is
	deleted, and in a separate try block. The second example below shows using a
	CArchive in this mode.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	This is a behavior of Visual C++ exception handling and did not occur with
	earlier versions of MFC, which did not use C++ exception handling.
	
	Sample Code
	-----------
	
	Example 1
	---------
	
	     // This example shows placing CFile, CArchive, and writes in separate
	     // try blocks
	     /* Compile options needed: default AppWizard application
	     */ 
	     void Test2()
	     {
	         try {
	             //Drive A: should contain a floppy with zero bytes free
	             CFile file("A:\\BadFile.tmp", CFile::modeCreate
	                        | CFile::shareExclusive | CFile::modeWrite );
	             try {
	                 CArchive archive(&file, CArchive::store);
	                 try {
	                     //Fill up disk, and cause a
	                     // CFileException::diskFull exception
	                     while(1)
	                         archive << (DWORD)17;
	                 }
	                 catch ( CFileException* ex ) {
	                     archive.Abort();
	                     ex->Delete();
	                 }
	                 catch (...){
	                     ASSERT(FALSE);
	                 }
	             }
	             catch ( CFileException* ex ) {
	                 file.Abort();
	                 ex->Delete();
	             }
	             catch (...){
	                  ASSERT(FALSE);
	             }
	         }
	         catch ( CFileException* ex ) {
	             ex->Delete();
	         }
	         catch (...){
	             ASSERT(FALSE);
	         }
	     }
	
	Example 2
	---------
	
	     // This example uses CArchive::bNoFlushOnDelete so that CFile and
	     // CArchive can be placed in the same try block.
	     /* Compile options needed: default AppWizard application
	     */ 
	     void Test3()
	     {
	          try {
	             //Drive A: should contain a floppy with zero bytes free
	             CFile file("A:\\BadFile.tmp",
	                 CFile::modeCreate | CFile::shareExclusive
	                             | CFile::modeWrite );
	             CArchive archive(&file,
	                 CArchive::store | CArchive::bNoFlushOnDelete);
	             try {
	                 //Fill up disk, and cause a CFileException::diskFull
	                 //exception
	                 while(1)
	                     archive << (DWORD)17;
	                 //Manually flush archive in try-block
	                 archive.Flush();
	             }
	             catch ( CFileException* ex ) {
	                 archive.Abort();
	                 ex->Delete();
	             }
	             catch (...){
	                 ASSERT(FALSE);
	             }
	         }
	         catch ( CFileException* ex ) {
	             ex->Delete();
	         }
	         catch (...){
	             ASSERT(FALSE);
	         }
	     }
	
	Additional query words: 2.00 2.10 2.20 4.00 4.10 4.20 kbdsd CArchive CFile Exception
	
	======================================================================
	Keywords          : kbFileIO kbMFC kbVC200 kbVC400 kbVC420 kbGrpDSMFCATL kbExceptHandCPP kbExceptHandling 
	Technology        : kbAudDeveloper kbMFC
	Version           : winnt:2.0,2.1,2.2,4.0,4.1,4.2
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
