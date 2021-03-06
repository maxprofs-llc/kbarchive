---
layout: page
title: "Q159823: HOWTO: Call Clipboard API from Visual Basic 4.0"
permalink: /kb/159/Q159823/
---

## Q159823: HOWTO: Call Clipboard API from Visual Basic 4.0

{% raw %}

	Article: Q159823
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kbcode kbVBp400 kbWndw
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article contains sample code that illustrates how to call Windows Clipboard
	API to copy a disk metafile to the Windows Clipboard using the 16-bit and 32-bit
	versions of Visual Basic 4.0. The code in the article can also be used to work
	around a bug in the SetData method of the Visual Basic Clipboard object. The
	workaround replaces the SetData method you use when you copy a disk metafile to
	clipboard.
	
	MORE INFORMATION
	================
	
	The following statement loads a metafile from a disk and copies it to the
	Windows Clipboard:
	
	     'DiskMetaFileName is the path to a WMF file on the disk.
	     Clipboard.SetData LoadPicture(DiskMetaFileName), vbCFMetafile
	
	The metafile is successfully copied to the Clipboard. However, the metafile size
	in the y dimension suggested in the disk metafile is ignored, and is set to
	match the suggested size in the x dimension. You can reproduce the bug by using
	the following code fragment with an Image control (Image1) on the form:
	
	     Clipboard.Clear                        ' Clear Clipboard.
	     Clipboard.SetData LoadPicture(DiskMetaFileName), vbCFMetafile
	     Image1.Stretch = False   'Resize the control to fit the graphics
	     Image1.Picture = Clipboard.GetData(vbCFMetafile) 'Copy from Clipboard
	     Debug.Print Image1.Width, Image1.Height
	
	NOTE: Image1.Width is always the same as Image1.Height.
	
	The sample code in this article provides a subroutine, SetMetaToClp, that works
	around the bug by directly calling Windows API.
	
	
	Step-by-Step Example
	--------------------
	
	1. Start Visual Basic 4.0. If it is already running, choose New Project from the
	  File menu. Form1 is created by default.
	
	2. Add two CommandButtons, Command1 and Command2, to Form1.
	
	3. Add one Image control, Image1, to Form1.
	
	4. Clear all the code for Form1, and then paste the following code to the code
	  window of Form1:
	
	  'Please change the path so that it points to a valid metafile.
	  Private Const strFileName = "d:\vb4\metafile\arrows\Smallarw.wmf"
	
	  Private Sub Command1_Click()
	      Clipboard.Clear                ' Clear Clipboard.
	      Clipboard.SetData LoadPicture(strFileName), vbCFMetafile
	      Image1.Stretch = False
	      Image1.Picture = Clipboard.GetData(vbCFMetafile) 'Copy from Clipboard
	      Debug.Print Image1.Width, Image1.Height
	  'Image1.Width is always the same as Image1.Height. Bug!
	
	  End Sub
	
	  Private Sub Command2_Click()
	      Clipboard.Clear                       ' Clear Clipboard.
	      SetMetaToClp strFileName
	      Image1.Stretch = False
	      Image1.Picture = Clipboard.GetData(vbCFMetafile) 'Copy from Clipboard
	      Debug.Print Image1.Width, Image1.Height
	
	  'Image1.Width and Image1.Height now display the metafile size suggested
	  'in the disk metafile
	  End Sub
	
	5. Insert a module, Module1, into the project. Copy and paste the following code
	  to Module1:
	
	  Public Const OFS_MAXPATHNAME = 128
	  Public Const OF_READ = &H0
	  Public Const GMEM_SHARE = &H2000
	  Public Const GMEM_MOVEABLE = &H2
	  Public Const GMEM_ZEROINIT = &H40
	  Public Const GHND = (GMEM_MOVEABLE Or GMEM_ZEROINIT)
	  Public Const HFILE_ERROR = &HFFFF
	
	  Type OFSTRUCT
	          cBytes As Byte
	          fFixedDisk As Byte
	          nErrCode As Integer
	          Reserved1 As Integer
	          Reserved2 As Integer
	          szPathName(OFS_MAXPATHNAME) As Byte
	  End Type
	
	  Type RECT
	          Left As Integer
	          Top As Integer
	          Right As Integer
	          Bottom As Integer
	  End Type
	
	  Type APMFILEHEADER
	      key As Long
	      hmf As Integer
	      bbox As RECT
	      inch As Integer
	      reserved As Long
	      checksum As Integer
	  End Type
	
	  #If Win16 Then
	    Type METAHEADER
	          mtType As Integer
	          mtHeaderSize As Integer
	          mtVersion As Integer
	          dummy1 As Integer
	          mtSize As Long
	          mtNoObjects As Integer
	          dummy2 As Integer
	          mtMaxRecord As Long
	          mtNoParameters As Integer
	    End Type
	
	    Type METAFILEPICT
	      mm As Integer
	      xExt As Integer
	      yExt As Integer
	      hmf As Integer
	    End Type
	  #Else
	    Type METAHEADER
	          mtType As Integer
	          mtHeaderSize As Integer
	          mtVersion As Integer
	          mtSize As Long
	          mtNoObjects As Integer
	          mtMaxRecord As Long
	          mtNoParameters As Integer
	    End Type
	
	    Type METAFILEPICT
	      mm As Long
	      xExt As Long
	      yExt As Long
	      hmf As Long
	    End Type
	  #End If
	
	  #If Win16 Then
	  Declare Function OpenClipboard Lib "User" (ByVal hwnd As Integer) _
	      As Integer
	  Declare Function CloseClipboard Lib "User" () As Integer
	  Declare Function EmptyClipboard Lib "User" () As Integer
	  Declare Function SetClipboardData Lib "User" (ByVal wFormat As _
	      Integer, ByVal hMem As Integer) As Integer
	  Declare Function GlobalAlloc Lib "Kernel" (ByVal wFlags As Integer, _
	      ByVal dwBytes As Long) As Integer
	  Declare Function GlobalLock Lib "Kernel" (ByVal hMem As Integer) As Long
	  Declare Function GlobalUnlock Lib "Kernel" (ByVal hMem As _
	  Integer) As Integer
	  Declare Function GlobalFree Lib "Kernel" (ByVal hMem As Integer) _
	  As Integer
	  Declare Sub CopyMemory Lib "Kernel" Alias "hmemcpy" (hpvDest As Any, _
	      ByVal hpvSource As Long, ByVal cbCopy As Long)
	  Declare Sub CopyMemory2 Lib "Kernel" Alias "hmemcpy" (ByVal hpvDest _
	      As Long, hpvSource As Any, ByVal cbCopy As Long)
	  Declare Function OpenFile Lib "Kernel" (ByVal lpFileName As String, _
	      lpReOpenBuff As OFSTRUCT, ByVal wStyle As Integer) As Integer
	  Declare Function llseek Lib "Kernel" Alias "_llseek" (ByVal hFile As _
	      Integer, ByVal lOffset As Long, ByVal iOrigin As Integer) As Long
	  Declare Function lread Lib "Kernel" Alias "_lread" (ByVal hFile As _
	  Integer, lpBuffer As Any, ByVal wBytes As Integer) As Integer
	  Declare Function lread2 Lib "Kernel" Alias "_lread" (ByVal hFile As _
	      Integer, ByVal lpBuffer As Long, ByVal wBytes As Integer) As Integer
	  Declare Function hread2 Lib "Kernel" Alias "_hread" (ByVal hFile As _
	      Integer, ByVal lpBuffer As Long, ByVal wBytes As Long) As Long
	  Declare Function lclose Lib "Kernel" Alias "_lclose" (ByVal hFile As _
	      Integer) As Integer
	  Declare Function SetMetaFileBits Lib "GDI" (ByVal hMem As _
	  Integer) As Integer
	  #Else
	  Declare Function OpenClipboard Lib "user32" (ByVal hwnd As Long) As Long
	  Declare Function CloseClipboard Lib "user32" () As Long
	  Declare Function EmptyClipboard Lib "user32" () As Long
	  Declare Function SetClipboardData Lib "user32" (ByVal wFormat As Long, _
	      ByVal hMem As Long) As Long
	  Declare Function GlobalAlloc Lib "Kernel32" (ByVal wFlags As Long, _
	      ByVal dwBytes As Long) As Long
	  Declare Function GlobalLock Lib "Kernel32" (ByVal hMem As Long) As Long
	  Declare Function GlobalUnlock Lib "Kernel32" (ByVal hMem As Long) As Long
	  Declare Function GlobalFree Lib "Kernel32" (ByVal hMem As Long) As Long
	  Declare Sub CopyMemory Lib "Kernel32" Alias "RtlMoveMemory" ( _
	      hpvDest As Any, ByVal hpvSource As Long, ByVal cbCopy As Long)
	  Declare Sub CopyMemory2 Lib "Kernel32" Alias "RtlMoveMemory" (ByVal _
	      hpvDest As Long, hpvSource As Any, ByVal cbCopy As Long)
	  Declare Function OpenFile Lib "Kernel32" (ByVal lpFileName As String, _
	      lpReOpenBuff As OFSTRUCT, ByVal wStyle As Long) As Long
	  Declare Function llseek Lib "Kernel32" Alias "_llseek" (ByVal hFile As _
	      Long, ByVal lOffset As Long, ByVal iOrigin As Long) As Long
	  Declare Function lread Lib "Kernel32" Alias "_lread" (ByVal hFile _
	      As Long, lpBuffer As Any, ByVal wBytes As Long) As Long
	  Declare Function lread2 Lib "Kernel32" Alias "_lread" (ByVal hFile _
	      As Long, ByVal lpBuffer As Long, ByVal wBytes As Long) As Long
	  Declare Function lclose Lib "Kernel32" Alias "_lclose" (ByVal hFile _
	      As Long) As Long
	  Declare Function SetMetaFileBitsEx Lib "gdi32" (ByVal nSize As Long, _
	      ByVal lpData As Long) As Long
	  #End If
	
	  Public Const CF_METAFILEPICT = 3
	
	  Public Const MM_ANISOTROPIC = 8
	  Public Const MM_ISOTROPIC = 7
	  Public Const MM_TWIPS = 6
	  Public Const MM_HIENGLISH = 5
	  Public Const MM_HIMETRIC = 3
	  Public Const MM_LOENGLISH = 4
	  Public Const MM_LOMETRIC = 2
	  Public Const MM_TEXT = 1
	
	  Public Sub SetMetaToClp(szFileName As String)
	      Dim inof As OFSTRUCT
	      Dim APMHeader As APMFILEHEADER
	      Dim mfHeader As METAHEADER
	  #If Win16 Then
	      Dim fh As Integer
	      Dim hData As Integer
	      Dim hmf As Integer
	      Dim hGlobal As Integer
	  #Else
	      Dim fh As Long
	      Dim hData As Long
	      Dim hmf As Long
	      Dim hGlobal As Long
	  #End If
	      fh = OpenFile(szFileName, inof, OF_READ)
	      If fh = HFILE_ERROR Then
	          Debug.Print "openfile fails"
	          Exit Sub
	      End If
	      llseek fh, 0, 0
	      lread fh, APMHeader, LenB(APMHeader)
	      llseek fh, LenB(APMHeader), 0
	      lread fh, mfHeader, LenB(mfHeader)
	
	      hData = GlobalAlloc(GHND, (mfHeader.mtSize * 2))
	      If hData = 0 Then
	          Debug.Print "fail to allocate memory"
	          lclose fh
	          Exit Sub
	      End If
	      Dim lpData As Long
	      lpData = GlobalLock(hData)
	      llseek fh, LenB(APMHeader), 0
	  #If Win16 Then
	      hread2 fh, lpData, mfHeader.mtSize * 2
	      GlobalUnlock (hData)
	      hmf = SetMetaFileBits(hData)
	  #Else
	      lread2 fh, lpData, mfHeader.mtSize * 2
	      hmf = SetMetaFileBitsEx(mfHeader.mtSize * 2, lpData)
	  #End If
	
	      lclose fh
	       'if any above file op's fail, hmf will be 0
	       'or you can check each file op return to see if it is HFILE_ERROR
	       'but that will be a big waste of code
	      If hmf = 0 Then
	          Debug.Print "openfile or SetMetaFile fails"
	          GlobalFree hData
	          Exit Sub
	      End If
	      Dim myMetaFilePict As METAFILEPICT
	      myMetaFilePict.mm = MM_ANISOTROPIC
	      myMetaFilePict.xExt = 2540& * (APMHeader.bbox.Right - _
	          APMHeader.bbox.Left) / APMHeader.inch
	      myMetaFilePict.yExt = 2540& * (APMHeader.bbox.Bottom - _
	          APMHeader.bbox.Top) / APMHeader.inch
	      myMetaFilePict.hmf = hmf
	   'cannot directly put myMetaFilePict to clipboard
	   'memory block for clipboard has to have the flag GMEM_SHARE
	      hGlobal = GlobalAlloc(GMEM_SHARE, LenB(myMetaFilePict))
	      Dim lpPict As Long
	      lpPict = GlobalLock(hGlobal)
	      CopyMemory2 lpPict, myMetaFilePict, LenB(myMetaFilePict)
	      GlobalUnlock hGlobal
	      OpenClipboard 0
	      EmptyClipboard
	      SetClipboardData CF_METAFILEPICT, hGlobal
	      CloseClipboard
	  End Sub
	
	(c) Microsoft Corporation 1996, All Rights Reserved.
	Contributions by Wei Hua, Microsoft Corporation
	
	
	======================================================================
	Keywords          : kbcode kbVBp400 kbWndw 
	Technology        : kbVBSearch kbAudDeveloper kbVB400Search kbVB400 kbVB16bitSearch
	Version           : 4.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
