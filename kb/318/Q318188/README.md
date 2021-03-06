---
layout: page
title: "Q318188: HOW TO: Save The Contents Of Visual Basic Form To a DIB Section"
permalink: /kb/318/Q318188/
---

## Q318188: HOW TO: Save The Contents Of Visual Basic Form To a DIB Section

{% raw %}

	Article: Q318188
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 
	Operating System(s): 
	Keyword(s): kbBitmap kbGDI kbSDKPlatform kbSDKWin32 kbDSupport kbGrpDSGDI kbHOWTOmaster kbgdip
	Last Modified: 28-MAR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, Version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, Version 6.0 
	-------------------------------------------------------------------------------
	
	
	IN THIS TASK
	
	- SUMMARY
	
	   - Save the Client Area to a DIB Section
	- Sample Code
	
	- REFERENCES
	
	SUMMARY
	=======
	
	This article demonstrates how to use the Graphics Device Interface (GDI)
	application programming interface (API) to save the client area of a Visual
	Basic form to a device-independent bitmap, known as a DIB section, that
	applications can write to directly. A DIB section, which you can create by
	calling the Windows API function CreateDIBSection(), allows device-independent
	modification of the bits because you have access to a pointer to the location of
	the bitmap's bit values.
	
	Save the Client Area to a DIB Section
	-------------------------------------
	
	To save the client area of a Visual Basic form to a DIB section, follow these
	steps:
	
	1. Use the GetDC() GDI API call to create a device context for the Visual Basic
	  form window's client area.
	
	2. Create a DIB section bitmap that is the same size as the Visual Basic form
	  window's client area.
	
	3. Use the CreateCompatibleDC() GDI API call to create a memory device context
	  that is compatible with the Visual Basic form window's device context that
	  you created in step 1.
	
	4. Use the SelectObject GDI API call to select the DIB section bitmap into the
	  memory device context.
	
	5. Use a GDI API call, such as BitBlt() or StretchBlt() to transfer the image
	  from the form's device context to the memory device context.
	
	Sample Code
	-----------
	
	To simplify the creation and use of DIB sections, a sample of code is available
	that contains most of the functionality in a dynamic link library (DLL). For
	additional information and to download this sample, click the article number
	below to view the article in the Microsoft Knowledge Base:
	
	  Q186221 SAMPLE: DibSectn.exe Uses DIBSections in Win32
	
	The sample code that follows uses this DLL to demonstrate the steps that are
	listed earlier, and then calls DSStoreDIBSectionInBMPFile from the DLL to store
	the DIB section to a file. You can use other functions in the DLL to make
	changes to the DIB section that you create, or you can use GDI API calls.
	
	        Private Const SRCCOPY = &HCC0020 ' (DWORD) dest = source
	
	        Private Declare Function DSCreateDIBSection Lib "dibsectn.dll" ( _
	           ByVal dwX As Long, _
	           ByVal dwY As Long, _
	           ByVal wBits As Integer) _
	        As Long
	
	        Private Declare Function DSStoreDIBSectionInBMPFile Lib "dibsectn.dll" ( _
	           ByVal szFileName As String, _
	           ByVal hBitmap As Long) _
	        As Boolean
	       
	        Private Declare Function StretchBlt Lib "gdi32" (ByVal hdc As Long, ByVal x As Long, _
	           ByVal y As Long, ByVal nWidth As Long, ByVal nHeight As Long, ByVal hSrcDC _
	           As Long, ByVal xSrc As Long, ByVal ySrc As Long, ByVal nSrcWidth As Long, _
	           ByVal nSrcHeight As Long, ByVal dwRop As Long) As Long
	
	        Private Declare Function GetDC Lib "user32" (ByVal hwnd As Long) As Long
	
	        Private Declare Function ReleaseDC Lib "user32" (ByVal hwnd As Long, _
	           ByVal hdc As Long) As Long
	
	        Private Declare Function CreateCompatibleDC Lib "gdi32" _
	           (ByVal hdc As Long) As Long
	        Private Declare Function DeleteDC Lib "gdi32" _
	           (ByVal hdc As Long) As Long
	
	        Private Declare Function SelectObject Lib "gdi32" _
	           (ByVal hdc As Long, ByVal hObject As Long) As Long
	
	        Private Declare Function DeleteObject Lib "gdi32" _
	           (ByVal hObject As Long) As Long
	
	              
	              Dim hdc As Long
	              Dim DibSection As Long
	              Dim hOldBitmap As Long
	              Dim hdcMem As Long
	              Dim Ret As Long
	              
	              hdc = GetDC(Form1.hwnd)
	              hdcMem = CreateCompatibleDC(hdc)
	
	              ' Call DSCreateDIBSection() from the DLL.
	              ' You can use the desired BPP in the last parameter(for example, 24)
	              DibSection = DSCreateDIBSection(Form1.ScaleWidth, Form1.ScaleHeight, 24)
	              hOldBitmap = SelectObject(hdcMem, DibSection)
	
	              Ret = StretchBlt(hdcMem, 0, 0, Form1.ScaleWidth, _
	                 Form1.ScaleHeight, hdc, 0, 0, Form1.ScaleWidth, _
	                 Form1.ScaleHeight, SRCCOPY)
	              If Ret = 0 Then GoTo Error
	              hOldBitmap = SelectObject(hdcMem, hOldBitmap)
	
	              ' Call DSStoreDIBSectionInBMPFile() from the DLL.
	              ' Add error handling.
	              Ret = DSStoreDIBSectionInBMPFile("c:\test.bmp", DibSection)
	              If Ret = 0 Then GoTo Error
	              Ret = ReleaseDC(Form1.hwnd, hdc)
	              If Ret = 0 Then GoTo Error
	              Ret = DeleteDC(hdcMem)
	              If Ret = 0 Then GoTo Error
	              Ret = DeleteObject(DibSection)
	              If Ret = 0 Then GoTo Error
	            
	  Error:
	              Debug.Print "Error"   ' Add error handling here.
	              
	  Success:
	              Debug.Print "Successful"
	
	REFERENCES
	==========
	
	For more information, see the following MSDN Web site:
	
	  Windows DDK: Graphics Device Interface
	  http://msdn.microsoft.com/library/default.asp?url=/library/en-us/wmeother/graphcnt_1lpv.asp
	
	Additional query words:
	
	======================================================================
	Keywords          : kbBitmap kbGDI kbSDKPlatform kbSDKWin32 kbDSupport kbGrpDSGDI kbHOWTOmaster kbgdip 
	Version           : :
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
