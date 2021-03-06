---
layout: page
title: "Q146022: HOWTO: Set Up the RichTextBox Control for WYSIWYG Printing"
permalink: /kb/146/Q146022/
---

## Q146022: HOWTO: Set Up the RichTextBox Control for WYSIWYG Printing

{% raw %}

	Article: Q146022
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 4.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kbprint kbtophit kbPrinting KbVBA kbVBp kbVBp400 kbVBp500 kbVBp600 kbGrpDSVB
	Last Modified: 05-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The SelPrint method of the RichTextBox control does not allow a programmer to
	set the position of the output on the printer. In addition, the RichTextBox
	control does not provide a method for displaying its contents as they would show
	up on the printer. This article explains how to set up a RichTextBox with a
	WYSIWYG (What You See Is What You Get) display and then how to print it.
	
	MORE INFORMATION
	================
	
	The Visual Basic RichTextBox control is a sub-classed control based on the
	RichTextBox provided by the Win32 operating system. The operating system control
	supports many messages that are not exposed in Visual Basic. One of these
	messages is EM_SETTARGETDEVICE. The EM_SETTARGETDEVICE message is used to tell a
	RichTextBox to base its display on a target device such as a printer. Another
	message that is not fully exposed by Visual Basic is EM_FORMATRANGE. The
	EM_FORMATRANGE message sends a page at a time to an output device using the
	specified coordinates. Using these messages in Visual Basic, it is possible to
	make a RichTextBox support WYSIWYG display and output.
	
	The following example illustrates how to take advantage of the EM_SETTARGETDEVICE
	and EM_FORMATRANGE messages from Visual Basic. The example provides two
	re-usable procedures to send these messages. The first procedure WYSIWYG_RTF()
	sets a RichTextBox to provide a WYSIWYG display based on the default printer and
	specified margins. The second procedure PrintRtf() prints the contents of the
	RichTextBox with the specified margins.
	
	EXAMPLE
	-------
	
	1. Start a new project in the Visual Basic 32-bit edition. Form1 is created by
	  default.
	
	2. Put a CommandButton and a RichTextBox control on Form1.
	
	3. Add the following code to Form1:
	
	  Private Const AnInch As Long = 1440   '1440 twips per inch
	  Private Const QuarterInch As Long = 360
	
	  Private Sub Form_Load()
	     Dim PrintableWidth As Long
	     Dim PrintableHeight As Long
	     Dim x As Single
	
	     ' Initialize Form and Command button
	     Me.Caption = "Rich Text Box WYSIWYG Printing Example"
	     Command1.Move 10, 10, 600, 380
	     Command1.Caption = "&Print"
	
	     ' Set the font of the RTF to a TrueType font for best results
	     RichTextBox1.SelFontName = "Arial"
	     RichTextBox1.SelFontSize = 10
	     
	     'initialize the printer object
	     x = Printer.TwipsPerPixelX
	     Printer.Orientation = vbPRORPortrait  'vbPRORLandscape
	
	     ' Tell the RTF to base it's display off of the printer
	     Call WYSIWYG_RTF(RichTextBox1, QuarterInch, QuarterInch, QuarterInch, QuarterInch, PrintableWidth, PrintableHeight) '1440 Twips=1 Inch
	
	     ' Set the form width to match the line width
	     Me.Width = PrintableWidth + 200
	     Me.Height = PrintableHeight + 800
	  End Sub
	
	  Private Sub Form_Resize()
	     ' Position the RTF on form
	     RichTextBox1.Move 100, 500, Me.ScaleWidth - 200, Me.ScaleHeight - 600
	  End Sub
	
	  Private Sub Command1_Click()
	     ' Print the contents of the RichTextBox with a one inch margin
	     PrintRTF RichTextBox1, AnInch, AnInch, AnInch, AnInch
	  End Sub
	
	4. Insert a new standard module into the project, Module1.bas is created by
	  default.
	
	5. Add the following code to Module1:
	
	  Option Explicit
	
	  Private Type Rect
	     Left As Long
	     Top As Long
	     Right As Long
	     Bottom As Long
	  End Type
	
	  Private Type CharRange
	    cpMin As Long     ' First character of range (0 for start of doc)
	    cpMax As Long     ' Last character of range (-1 for end of doc)
	  End Type
	
	  Private Type FormatRange
	    hdc As Long       ' Actual DC to draw on
	    hdcTarget As Long ' Target DC for determining text formatting
	    rc As Rect        ' Region of the DC to draw to (in twips)
	    rcPage As Rect    ' Region of the entire DC (page size) (in twips)
	    chrg As CharRange ' Range of text to draw (see above declaration)
	  End Type
	
	  Private Const WM_USER As Long = &H400
	  Private Const EM_FORMATRANGE As Long = WM_USER + 57
	  Private Const EM_SETTARGETDEVICE As Long = WM_USER + 72
	  Private Const PHYSICALOFFSETX As Long = 112
	  Private Const PHYSICALOFFSETY As Long = 113
	
	  Private Declare Function GetDeviceCaps Lib "gdi32" ( _
	     ByVal hdc As Long, ByVal nIndex As Long) As Long
	  Private Declare Function SendMessage Lib "USER32" Alias "SendMessageA" _
	     (ByVal hWnd As Long, ByVal msg As Long, ByVal wp As Long, _
	     lp As Any) As Long
	  Private Declare Function CreateDC Lib "gdi32" Alias "CreateDCA" _
	     (ByVal lpDriverName As String, ByVal lpDeviceName As String, _
	     ByVal lpOutput As Long, ByVal lpInitData As Long) As Long
	
	  ''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
	  '
	  ' WYSIWYG_RTF - Sets an RTF control to display itself the same as it
	  '               would print on the default printer
	  '
	  ' RTF - A RichTextBox control to set for WYSIWYG display.
	  '
	  ' LeftMarginWidth - Width of desired left margin in twips
	  '
	  ' RightMarginWidth - Width of desired right margin in twips
	  '
	  ' Returns - The length of a line on the printer in twips
	  '''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
	  Public Sub WYSIWYG_RTF(RTF As RichTextBox, LeftMarginWidth As Long, RightMarginWidth As Long, TopMarginWidth As Long, BottomMarginWidth As Long, PrintableWidth As Long, PrintableHeight As Long)
	     Dim LeftOffset As Long
	     Dim LeftMargin As Long
	     Dim RightMargin As Long
	     Dim TopOffset As Long
	     Dim TopMargin As Long
	     Dim BottomMargin As Long
	     Dim PrinterhDC As Long
	     Dim r As Long
	
	     ' Start a print job to initialize printer object
	     Printer.Print Space(1)
	     Printer.ScaleMode = vbTwips
	     
	     ' Get the left offset to the printable area on the page in twips
	     LeftOffset = GetDeviceCaps(Printer.hdc, PHYSICALOFFSETX)
	     LeftOffset = Printer.ScaleX(LeftOffset, vbPixels, vbTwips)
	     
	     ' Calculate the Left, and Right margins
	     LeftMargin = LeftMarginWidth - LeftOffset
	     RightMargin = (Printer.Width - RightMarginWidth) - LeftOffset
	     
	     ' Calculate the line width
	     PrintableWidth = RightMargin - LeftMargin
	     
	     ' Get the top offset to the printable area on the page in twips
	     TopOffset = GetDeviceCaps(Printer.hdc, PHYSICALOFFSETY)
	     TopOffset = Printer.ScaleX(TopOffset, vbPixels, vbTwips)
	     
	     ' Calculate the Left, and Right margins
	     TopMargin = TopMarginWidth - TopOffset
	     BottomMargin = (Printer.Height - BottomMarginWidth) - TopOffset
	     
	     ' Calculate the line width
	     PrintableHeight = BottomMargin - TopMargin
	      
	     
	     ' Create an hDC on the Printer pointed to by the Printer object
	     ' This DC needs to remain for the RTF to keep up the WYSIWYG display
	     PrinterhDC = CreateDC(Printer.DriverName, Printer.DeviceName, 0, 0)
	
	     ' Tell the RTF to base it's display off of the printer
	     '    at the desired line width
	     r = SendMessage(RTF.hWnd, EM_SETTARGETDEVICE, PrinterhDC, _
	        ByVal PrintableWidth)
	
	     ' Abort the temporary print job used to get printer info
	     Printer.KillDoc
	  End Sub
	
	  ''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
	  '
	  ' PrintRTF - Prints the contents of a RichTextBox control using the
	  '            provided margins
	  '
	  ' RTF - A RichTextBox control to print
	  '
	  ' LeftMarginWidth - Width of desired left margin in twips
	  '
	  ' TopMarginHeight - Height of desired top margin in twips
	  '
	  ' RightMarginWidth - Width of desired right margin in twips
	  '
	  ' BottomMarginHeight - Height of desired bottom margin in twips
	  '
	  ' Notes - If you are also using WYSIWYG_RTF() on the provided RTF
	  '         parameter you should specify the same LeftMarginWidth and
	  '         RightMarginWidth that you used to call WYSIWYG_RTF()
	  ''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
	  Public Sub PrintRTF(RTF As RichTextBox, LeftMarginWidth As Long, _
	     TopMarginHeight, RightMarginWidth, BottomMarginHeight)
	     Dim LeftOffset As Long, TopOffset As Long
	     Dim LeftMargin As Long, TopMargin As Long
	     Dim RightMargin As Long, BottomMargin As Long
	     Dim fr As FormatRange
	     Dim rcDrawTo As Rect
	     Dim rcPage As Rect
	     Dim TextLength As Long
	     Dim NextCharPosition As Long
	     Dim r As Long
	
	     ' Start a print job to get a valid Printer.hDC
	     Printer.Print Space(1)
	     Printer.ScaleMode = vbTwips
	
	     ' Get the offsett to the printable area on the page in twips
	     LeftOffset = Printer.ScaleX(GetDeviceCaps(Printer.hdc, _
	        PHYSICALOFFSETX), vbPixels, vbTwips)
	     TopOffset = Printer.ScaleY(GetDeviceCaps(Printer.hdc, _
	        PHYSICALOFFSETY), vbPixels, vbTwips)
	
	     ' Calculate the Left, Top, Right, and Bottom margins
	     LeftMargin = LeftMarginWidth - LeftOffset
	     TopMargin = TopMarginHeight - TopOffset
	     RightMargin = (Printer.Width - RightMarginWidth) - LeftOffset
	     BottomMargin = (Printer.Height - BottomMarginHeight) - TopOffset
	
	     ' Set printable area rect
	     rcPage.Left = 0
	     rcPage.Top = 0
	     rcPage.Right = Printer.ScaleWidth
	     rcPage.Bottom = Printer.ScaleHeight
	
	     ' Set rect in which to print (relative to printable area)
	     rcDrawTo.Left = LeftMargin
	     rcDrawTo.Top = TopMargin
	     rcDrawTo.Right = RightMargin
	     rcDrawTo.Bottom = BottomMargin
	
	     ' Set up the print instructions
	     fr.hdc = Printer.hdc   ' Use the same DC for measuring and rendering
	     fr.hdcTarget = Printer.hdc  ' Point at printer hDC
	     fr.rc = rcDrawTo            ' Indicate the area on page to draw to
	     fr.rcPage = rcPage          ' Indicate entire size of page
	     fr.chrg.cpMin = 0           ' Indicate start of text through
	     fr.chrg.cpMax = -1          ' end of the text
	
	     ' Get length of text in RTF
	     TextLength = Len(RTF.Text)
	
	     ' Loop printing each page until done
	     Do
	        ' Print the page by sending EM_FORMATRANGE message
	        NextCharPosition = SendMessage(RTF.hWnd, EM_FORMATRANGE, True, fr)
	        If NextCharPosition >= TextLength Then Exit Do  'If done then exit
	        fr.chrg.cpMin = NextCharPosition ' Starting position for next page
	        Printer.NewPage                  ' Move on to next page
	        Printer.Print Space(1) ' Re-initialize hDC
	        fr.hdc = Printer.hdc
	        fr.hdcTarget = Printer.hdc
	     Loop
	
	     ' Commit the print job
	     Printer.EndDoc
	
	     ' Allow the RTF to free up memory
	     r = SendMessage(RTF.hWnd, EM_FORMATRANGE, False, ByVal CLng(0))
	  End Sub
	
	6. Save the project.
	
	7. Run the project.
	
	8. Enter or paste some text into the RichTextBox.
	
	9. Press the Print command button. Note that the printed output should word-wrap
	  at the same locations as displayed on the screen. Also, the output should be
	  printed with the specified one-inch margin all around.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbprint kbtophit kbPrinting KbVBA kbVBp kbVBp400 kbVBp500 kbVBp600 kbGrpDSVB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVB500 kbVB600 kbVB400Search kbVB400
	Version           : :4.0,5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
