---
layout: page
title: "Q136302: FIX: Drop-down Combobox Does Not Move with Property Sheet"
permalink: /kb/136/Q136302/
---

## Q136302: FIX: Drop-down Combobox Does Not Move with Property Sheet

{% raw %}

	Article: Q136302
	Product(s): Microsoft C Compiler
	Version(s): WINDOWS:1.52,1.52b; winnt:2.0,2.1,2.2
	Operating System(s): 
	Keyword(s): kbcode kbComboBox kbMFC kbPropSheet KbUIDesign kbVC152fix kbVC200fix kbVC210fix kbVC220
	Last Modified: 08-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, versions 1.52, 1.52b, 2.0, 2.1, 2.2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When a combo box on the active page of a CPropertySheet object is opened and the
	property sheet is moved by dragging it with the mouse, the drop-down portion of
	the combo box stays at its current screen position; it does not move with the
	underlying property sheet's dialog box.
	
	NOTE: This bug consistently occurs in 16-bit applications running under Windows
	95 or Windows version 3.x. However, it does not occur when running under Windows
	NT, and it occurs intermittently in 32-bit applications running under Windows
	95.
	
	CAUSE
	=====
	
	The _AfxCancelModes internal MFC function is not called from
	CPropertySheet::PreTranslateMessage() as it is for CFrameWnd. In 32-bit Visual
	C++, _AfxCancelModes is defined as AfxCancelModes.
	
	RESOLUTION
	==========
	
	To work around this problem, derive a class from CPropertySheet and call
	_AfxCancelModes from the derived class's PreTranslateMessage when the
	WM_LBUTTONDOWN or WM_NCLBUTTONDOWN messages are received. See the "Step- By-Step
	Workaround" section in this article for an example.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This problem was corrected in Microsoft Visual C++,
	32-bit Edition, version 4.0.
	
	MORE INFORMATION
	================
	
	Step-By-Step Workaround
	-----------------------
	
	1. Create a new class derived from CPropertySheet.
	
	  1. Open the ClassWizard.
	
	  2. Click the Add Class button.
	
	  3. Choose a Class Type of generic CWnd. This is necessary because ClassWizard
	     does not support creating a CPropertySheet class in 16-bit Visual C++. If
	     you are using 32-bit Visual C++, you should be able to derive a class from
	     CPropertySheet directly.
	
	  4. Enter a Class Name such as CMySheet.
	
	  5. Click the Create Class button.
	
	2. If you are using 32-bit Visual C++, please skip steps 2.a, 2.b, and 2.c. In
	  the new .h file (mysheet.h), make these changes:
	
	  1. Change this:
	
	           class CMySheet : public CWnd
	
	     To this:
	
	           class CMySheet : public CPropertySheet
	
	  2. Add the following as the first line in the class definition:
	
	        DECLARE_DYNAMIC(CMySheet)
	
	  3. Delete the default constructor declaration and add the following two
	     constructors in its place:
	
	        CMySheet(UINT nIDCaption, CWnd *pParentWnd = NULL,
	           UINT iSelectPage = 0 ) : CPropertySheet(nIDCaption,
	           pParentWnd, iSelectPage) { }
	        CMySheet(LPCTSTR pszCaption, CWnd *pParentWnd = NULL,
	           UINT iSelectPage = 0 ) : CPropertySheet(pszCaption,
	           pParentWnd, iSelectPage) { }
	
	  4. Add a prototype for an override of PreTranslateMessage in a public section
	     of the class definition:
	
	        public:
	            virtual BOOL PreTranslateMessage(MSG* pMsg);
	
	3. If you are using 32-bit Visual C++, please skip step 3.a. In the new .cpp
	  file (mysheet.cpp), make these changes:
	
	  1. Delete the default constructor function body.
	
	  2. Add the definition of PreTranslateMessage:
	
	        BOOL CMySheet::PreTranslateMessage(MSG* pMsg)
	        {
	            // check for special cancel modes for ComboBoxes
	            if (pMsg->message == WM_LBUTTONDOWN ||
	            pMsg->message == WM_NCLBUTTONDOWN)
	          _AfxCancelModes(pMsg->hwnd);    // filter clicks
	
	         return CPropertySheet::PreTranslateMessage(pMsg);
	        }
	
	  3. Use The following sample code to define _AfxCanelModes. Place this code
	     should be placed above the CMySheet::PreTranslateMessage definition. The
	     code is needed because if the project is linking to the DLL version of
	     MFC, you need to copy the code for this function and one other function
	     that is called and insert it into the project. The code can be found in
	     msvc\mfc\src\winutil.cpp. If the project links to a static MFC library,
	     all you need to do is add a prototype for the function. The code handles
	     both situations by using the #ifdef - #else - #endif preprocessor
	     directives.
	
	        /* Compile options needed: Default AppWizard options
	        */ 
	
	        #ifdef _AFXDLL  // define the functions
	        BOOL PASCAL _AfxIsComboBoxControl(HWND hWnd, UINT nStyle)
	        {
	           if (hWnd == NULL)
	           return FALSE;
	           // do cheap style compare first
	           if ((UINT)(::GetWindowLong(hWnd, GWL_STYLE) & 0x0F) != nStyle)
	           return FALSE;
	
	           // do expensive classname compare next
	
	           // If using 16-bit Visual C++, use the following code
	              static char BASED_CODE szComboBox[] = "combobox";
	              char szCompare[sizeof(szComboBox) + 1];
	              ::GetClassName(hWnd, szCompare, sizeof(szCompare));
	
	            // else if using 32-bit Visual C++, use the following code
	            // and comment out the code above.
	            // 
	            //  static const TCHAR szComboBox[] = _T("combobox");
	            //  TCHAR szCompare[sizeof(szComboBox)/sizeof(szCompare[0])+1];
	            //  ::GetClassName(hWnd, szCompare,
	            //                 sizeof(szCompare)/sizeof(szCompare[0]) );
	
	            return (lstrcmpi(szCompare, szComboBox) == 0);
	              }
	
	            void PASCAL _AfxCancelModes(HWND hWndRcvr)
	            {
	            // if we receive a message destined for a window, cancel any
	            // combobox popups that could be in toolbars or dialog bars
	            HWND hWndCancel = ::GetFocus();
	            if (hWndCancel == NULL)
	            return;     // nothing to cancel
	
	            if (hWndCancel == hWndRcvr)
	            return;     // let input go to window with focus
	
	            // focus is in part of a combo-box
	            if (!_AfxIsComboBoxControl(hWndCancel, (UINT)CBS_DROPDOWNLIST))
	            {
	            // try as a dropdown
	            hWndCancel = ::GetParent(hWndCancel);// parent of edit is combo
	            if (hWndCancel == hWndRcvr)
	            return;     // let input go to part of combo
	
	            if (!_AfxIsComboBoxControl(hWndCancel, (UINT)CBS_DROPDOWN))
	               return;     // not a combo-box that is active
	            }
	
	            // combo-box is active, but if receiver is a popup, do nothing
	            if (hWndRcvr != NULL &&
	              (::GetWindowLong(hWndRcvr, GWL_STYLE) & WS_CHILD) != 0 &&
	              ::GetParent(hWndRcvr) == ::GetDesktopWindow())
	            return;
	
	            // finally, you should cancel the mode !
	            ::SendMessage(hWndCancel, CB_SHOWDROPDOWN, FALSE, 0L);
	        }
	
	        #else   // just prototype it
	        void PASCAL _AfxCancelModes(HWND hWndRcvr);
	
	        #endif
	
	NOTE: In your application, make sure you use class CMySheet instead of the
	default CPropertySheet.
	
	Additional query words: 2.00 2.51 2.52 3.00 3.10 3.20
	
	======================================================================
	Keywords          : kbcode kbComboBox kbMFC kbPropSheet KbUIDesign kbVC152fix kbVC200fix kbVC210fix kbVC220fix kbGrpDSMFCATL 
	Technology        : kbVCsearch kbAudDeveloper kbVC220 kbVC200 kbVC210 kbVC152 kbVC152a
	Version           : WINDOWS:1.52,1.52b; winnt:2.0,2.1,2.2
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
