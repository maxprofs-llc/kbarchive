---
layout: page
title: "Q179137: Enable Default Processing in a Subclassed Button Control"
permalink: /kb/179/Q179137/
---

## Q179137: Enable Default Processing in a Subclassed Button Control

{% raw %}

	Article: Q179137
	Product(s): Microsoft C Compiler
	Version(s): 5.0,6.0
	Operating System(s): 
	Keyword(s): kbfile kbSample kbActiveX kbButton kbCOMt kbCtrlCreate kbDlg kbKeyAccel kbMFC kbVC500 k
	Last Modified: 26-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, 32-bit Enterprise Edition, versions 5.0, 6.0 
	- Microsoft Visual C++, 32-bit Professional Edition, versions 5.0, 6.0 
	- Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	- Microsoft Visual C++.NET (2002) 
	-------------------------------------------------------------------------------
	
	NOTE: Microsoft Visual C++ .NET (2002) supports both the managed code model that is provided by the Microsoft .NET Framework and the unmanaged native Microsoft Windows code model. The information in this article applies to unmanaged Visual C++ code only.
	
	SUMMARY
	=======
	
	This article describes how to ensure default command processing when subclassing
	the standard Windows Button control to create an MFC ActiveX control. It also
	discusses how to determine when a control is the default command in both design-
	and run-time modes so that the control is drawn correctly. Finally, the article
	addresses how to ensure that the ENTER key gets routed to the current default
	command.
	
	MORE INFORMATION
	================
	
	The following files are available for download from the Microsoft Download
	Center:
	
	Visual C++ 6.0:
	
	  DownloadDownload Defbutn.exe now
	  (http://download.microsoft.com/download/vc60pro/Sample/1/NT4/EN-US/DefButn.exe)
	
	For additional information about how to download Microsoft Support files, click
	the following article number to view the article in the Microsoft Knowledge
	Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft scanned this file for viruses. Microsoft used the most current
	virus-detection software that was available on the date that the file was
	posted. The file is stored on secure servers that prevent any unauthorized
	changes to the file.
	
	Visual C++ .NET:
	
	The following file is available for download from the Microsoft Download Center:
	
	  DownloadDownload Defbutnvcnet.exe now
	  (http://download.microsoft.com/download/VisualStudioNET/Sample/1.4/WIN98MeXP/EN-US/Defbutnvcnet.exe)
	
	Release Date: June 25, 2002
	
	For additional information about how to download Microsoft Support files, click
	the following article number to view the article in the Microsoft Knowledge
	Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft scanned this file for viruses. Microsoft used the most current
	virus-detection software that was available on the date that the file was
	posted. The file is stored on secure servers that prevent any unauthorized
	changes to the file.
	
	
	The following sections and the DefButn.exe sample code describe how to:
	
	- Make a Subclassed Control That Supports Extended Properties
	
	- Set a Control to Be the Default Command at Run Time
	
	- Use the Caption Property to Display the Command Text
	
	- Draw Correctly Depending Upon Default Command Status
	
	- Ensure That the ENTER Key Gets Routed to the Current Default Command
	
	Make a Subclassed Control That Supports Extended Properties
	-----------------------------------------------------------
	
	To create a control that supports extended properties so that the container can
	display its extended Default property in the Property Browser window when the
	control is selected at design time, do the following:
	
	1. Use the MFC ActiveX ControlWizard in Microsoft Visual C++ to create a new
	  project called DefBtn.
	
	2. Accept all defaults in step 1.
	
	3. In step 2, select the Button control in response to "Which window class, if
	  any, should this control subclass?" and accept all other defaults.
	
	4. Click Finish to create the control.
	
	5. In DefBtnctl.cpp add the following miscellaneous status bit to the
	  _dwDefBtnOleMisc bit mask:
	
	        OLEMISC_ACTSLIKEBUTTON
	
	  This allows a container that supports extended properties, such as Visual
	  Basic, to present the Default extended property in its Property Browser
	  window during design time. When using the control in an application, a
	  programmer can make your control the default command by setting this property
	  to "True." Note that in an environment that does not support extended
	  properties, such as Visual C++, this flag has no effect.
	
	Set a Control to Be the Default Command at Run Time
	---------------------------------------------------
	
	To set the default command at run time in an MFC dialog-based container
	application that does not support extended properties, add the following call to
	the OnInitDialog processing:
	
	     CDialog::SetDefID
	
	and pass in the control ID of DefBtn. This will override any other control that
	was selected as the default command at design time. You do not need to make any
	modifications to the control[ASCII 146]s source code nor to its property page.
	
	Use the Caption Property to Display the Command Text
	----------------------------------------------------
	
	To display the command text both at run time and design time, do the following:
	
	1. Expose the stock Caption property using ClassWizard. The subclassed control
	  automatically draws this property at run time.
	
	2. To display the text at design time you have to include drawing code in the
	  CDefBtnCtrl::OnDraw member function to check whether the UserMode ambient
	  property is set to "False" (indicating design mode).
	
	3. Use the CDC::GetInternalText member function to get the current value of the
	  Caption stock property and draw it using the CDC::DrawText member function.
	
	Draw Correctly Depending Upon Default Command Status
	----------------------------------------------------
	
	ActiveX controls implement functionality that the older, pre-Ole Windows controls
	(such as the Button control) do not. Because the MFC method of subclassing a
	control is a way to support older technology, there tend to be inconsistencies
	in certain operations (especially drawing) between subclassed controls and those
	developed without subclassing. For example, the Button control does not draw its
	border in accordance with Windows 95 user interface guidelines for a default
	command.
	
	You can add logic to a subclassed control so that its border is drawn to reflect
	the default command status. Look at various CDC member functions such as
	DrawEdge to do so. Note that the DefButn.exe sample does not include the code to
	do this.
	
	The DefButn.exe sample does include the logic to detect any change in the default
	command status when overriding the CDefBtnCtrl::OnAmbientPropertyChange member
	function. To determine when a control has been set as the default command on a
	form at design time, and to draw correctly depending upon the default command
	status in both design- and run-time modes, do the following:
	
	1. If the DISPID of the ambient property passed in is:
	
	        DISPID_AMBIENT_DISPLAYASDEFAULT
	
	  then obtain the value it changed to by calling the GetAmbientProperty
	  function.
	
	2. Pass in this DISPID and the address of a BOOL class member variable called
	  m_bDefault. If "True," the control becomes the default button; "False" means
	  it is no longer the default button.
	
	3. Call the InvalidateControl function to redraw the control (use
	  CDefBtnCtrl::OnDraw) with the shadow outline border that indicates that a
	  command is the default. Use the value of m_bDefault to determine whether you
	  should draw the outline (True) or remove it (False).
	
	Note that the control draws correctly with respect to focus (user has tabbed to
	it). There is no need to manually draw the interior dotted rectangle.
	
	Ensure That the ENTER Key Gets Routed to the Current Default Command
	--------------------------------------------------------------------
	
	This section describes how to receive the WM_COMMAND message when the ENTER key
	is pressed, and the default command is a subclassed control. In Microsoft Visual
	C++ Books Online, "Programming with MFC: Encyclopedia," the article called
	"Keyboard Interface" contains the following paragraph:
	
	  The container traps the ENTER and ESC keys by including them in its
	  accelerator table. When one of these keys is pressed, the container
	  calls the standard method Click in the appropriate control's primary
	  dispatch interface. The standard Click method is described in Control
	  Methods.
	
	If you want to do special processing within your control when the ENTER key is
	pressed and your control is the default command, you must use the ClassWizard to
	expose the DoClick custom method. You should send the Click event back to the
	container when your control[ASCII 146]s DoClick method has been called. Use
	ClassWizard to expose the Click stock event and call the FireClick() event from
	within the CDefBtnCtrl::DoClick() member function to do this.
	
	If no special processing is needed and you just want to ensure that the Click
	event gets fired back to the container, then expose the DoClick stock method and
	the Click stock event. In MFC's default processing, FireClick will be called for
	you.
	
	Additional query words: 4.20 Defbutn Defbutnvcnet
	
	======================================================================
	Keywords          : kbfile kbSample kbActiveX kbButton kbCOMt kbCtrlCreate kbDlg kbKeyAccel kbMFC kbVC500 kbVC600 kbWndwClass kbGrpDSMFCATL kbDialog kbAcceleratorKey 
	Technology        : kbVCsearch kbAudDeveloper kbVC500 kbVC600 kbVC32bitSearch kbVCNET kbVC500Search
	Version           : :5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
