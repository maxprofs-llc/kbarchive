---
layout: page
title: "Q208568: HOWTO: Access Pocket Outlook Objects from VBCE"
permalink: /kb/208/Q208568/
---

## Q208568: HOWTO: Access Pocket Outlook Objects from VBCE

{% raw %}

	Article: Q208568
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 3.01
	Operating System(s): 
	Keyword(s): kbOutlook kbToolkit kbVBp600 kbOSWinCEsearch kbGrpDSVB
	Last Modified: 13-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows CE Toolkit for Visual Basic 6.0 
	- Microsoft Pocket Outlook, version 3.01 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The purpose of this article is to introduce developers who use the Microsoft
	Windows CE Toolkit for Visual Basic 6.0 to the Pocket Outlook Object Model
	(POOM) SDK. The following topics are covered:
	
	1. What is the Pocket Outlook Object Model (POOM) SDK?
	2. Where to obtain the POOM SDK.
	3. How to install and register the POOM SDK on a device.
	4. An overview of the POOM.
	5. How to begin programming with the POOM SDK:
	
	   - How to logon and logoff.
	   - How to create a new contact.
	   - How to view information about a contact.
	   - How to obtain a list of contacts.
	   - How to create an appointment.
	   - How to obtain appointment information.
	   - How to create a task.
	   - How to obtain task information.
	   - How to add a city.
	   - How to obtain city and time zone information.
	   - How to specify a home and visiting city.
	   - How to send items via Infrared transfer.
	   - How to receive items via Infrared transfer.
	
	MORE INFORMATION
	================
	
	1. What is the Pocket Outlook Object Model (POOM) SDK?
	
	  The Pocket Outlook Object Model SDK is the means by which the object model for
	  Pocket Outlook is exposed to programmers using the Windows CE Toolkit for
	  Visual Basic 6.0 (VBCE6) and the Windows CE Toolkit for Visual C++ 6.0
	  (VCCE6). This allows for programmatic manipulation of Contact, Calendar and
	  Task data as well as the capability to view City and TimeZone information.
	2. Where to obtain the POOM SDK.
	
	  The POOM SDK can be downloaded from the following Microsoft Web site:
	
	  Pocket Outlook Object Model (POOM) SDK Download
	  htt p://www.microsoft.com/mobile/downloads/developer/poomsdk.asp
	
	3. How to install and register the POOM SDK on a device.
	
	  Once the POOM SDK has been downloaded, run the pimstore.exe file to extract
	  its contents. To use the POOM, you need to install and register
	  "pimstore.dll" on your Windows CE Companion device. The DLL for each CPU is
	  copied to your PC when you download and run the self-extracting .exe file.
	  The DLLs are distinguished by name; for example, pimstore_sh3.dll supports
	  the SH3 processor. To use POOM, drag the "pimstore_*.dll" for your CPU to the
	  \Windows directory of your companion device. Rename the DLL to "pimstore.dll"
	  without the underscore and CPU designation.
	
	  You'll need to register the pimstore.dll on the device. This can be
	  accomplished in a couple of different ways including running regsvr.exe on
	  the device as follows:
	
		\windows\regsvr.exe \windows\pimstore.dll
	
	  If your device does not have a regsvr.exe utility, a third-party registry tool
	  is available from: http://www.cega dgets.com/files/controls/regsvr2.zip
	
	  Another alternative is to compile the sample code that is listed in the POOM
	  SDK ReadMe.txt file.
	4. Emulation.
	
	  The POOM SDK does not support Windows CE emulation at this time.
	5. An overview of the POOM.
	
	  The Pocket Outlook Object Model is modeled after the Outlook 97 and 98 Object
	  Models on the desktop. In order to provide a smaller DLL more suited for
	  Windows CE devices, POOM is a smaller subset of the desktop Outlook Object
	  Model.
	
	  The Pocket Outlook Object Model meets the following goals:
	
	  1. Backward compatibility. The component runs on H/PC 2.0, H/PC 3.0, and P/PC
	     1.0, allowing applications to be written for those devices. To achieve
	     this, the component exists on top of existing components that haven't
	     changed since H/PC 2.0.
	
	  2. Future extensibility. The interfaces are designed to be extensible in the
	     future. For example, there is a Folder object, which in this version is
	     little more than a wrapper around a database. Because of the first goal,
	     you cannot create or otherwise manipulate these folders, but that is
	     something that could be allowed in future versions.
	
	  3. Outlook compatibility. Although based on the desktop edition of the
	     Outlook Object Model, there are some differences that exist to achieve
	     simplicity on the device. For example, a NameSpace object is not provided,
	     which Outlook uses to log on to a MAPI session, and which would just be an
	     extra layer on Windows CE devices. It would be more accurate to say that
	     the Pocket Outlook Object Model is based on the desktop Outlook Object
	     Model rather than to say it is a subset of the model.
	
	  4. Automation object. In order to allow Visual Basic and scripting
	     programmers the ability to use the Object Model, it has an automation
	     object with a dual interface. Although the method and property names are a
	     little more complicated in C or C++ than they are in Visual Basic, this
	     was an important trade-off for customers.
	
	  5. Simplicity. The interfaces are meant to be quite simple, and as such,
	     represent a small subset of the desktop Outlook Object Model
	     functionality.
	
	  The main interface to the Pocket Outlook Object Model is the Pocket Outlook
	  Application object. It is from this object that all other objects are
	  derived. After logging on to the Application object, you can access various
	  Folder objects.
	
	  A Folder object contains a collection of Items. This folder implementation is
	  a subset of Outlook's Folder object. The Folder object is a wrapper for the
	  Contacts, Clock, Calendar, and Tasks databases. There is only one folder for
	  each type of item. The Folder object itself cannot be created or otherwise
	  manipulated. The Folder object is provided mainly for compatibility with
	  Outlook. An Infrared Folder is also provided, which you can use to send items
	  over an IR port.
	
	  From the Folder object, you get the Items collection. An Items collection is,
	  as the name implies, a collection of Contacts, Tasks, Appointments, or
	  Cities. From an Items collection, you can retrieve or create individual
	  items. The Items collection also allows you to do basic filtering over a
	  collection of objects.
	
	  With an individual Item, you can set and retrieve individual properties. You
	  can create, modify, or delete an item in the store. Note that Cities are
	  read-only items and cannot be created or modified.
	
	  Task and Appointment items support the RecurrencePattern object. The
	  RecurrencePattern object lets you set up a recurrence for a task or
	  appointment. Appointments also support the Recipients collection, which
	  allows you to specify recipients for a meeting. If an appointment has a
	  recipients collection, it is a meeting request.
	
	  The following table represents the basic Pocket Outlook Object Model:
	
	  +--------------------------------------------------+
	  | Application Object |               |          |  | 
	  +--------------------------------------------------+
	  |                    | Folder Object |          |  | 
	  +--------------------------------------------------+
	  |                    |               | Calendar |  | 
	  +--------------------------------------------------+
	  |                    |               | Cities   |  | 
	  +--------------------------------------------------+
	  |                    |               | Contacts |  | 
	  +--------------------------------------------------+
	  |                    |               | Infrared |  | 
	  +--------------------------------------------------+
	  |                    |               | Tasks    |  | 
	  +--------------------------------------------------+
	
	6. How to Begin Programming with the POOM SDK:
	
	  Microsoft provides programming examples for illustration only, without
	  warranty either expressed or implied, including, but not limited to, the
	  implied warranties of merchantability and/or fitness for a particular
	  purpose. This article assumes that you are familiar with the programming
	  language being demonstrated and the tools used to create and debug
	  procedures. Microsoft support professionals can help explain the
	  functionality of a particular procedure, but they will not modify these
	  examples to provide added functionality or construct procedures to meet your
	  specific needs. If you have limited programming experience, you may want to
	  contact a Microsoft Certified Partner or the Microsoft fee-based consulting
	  line at (800) 936-5200. For more information about Microsoft Certified
	  Partners, please visit the following Microsoft Web site:
	
	  http://www.microsoft.com/partner/referral/
	
	  For more information about the support options that are available and about
	  how to contact Microsoft, visit the following Microsoft Web site:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	  Before you start programming using the POOM, it might be helpful to set a
	  reference to the DLL in order to utilize Intellisense Help. To do this, from
	  the Project menu, select References and browse until you find the
	  pimstore_i486.dll file that shipped with the POOM.
	
	   - How to log on and log off.
	
	     Logon and Logoff should be the first and last things called, respectively,
	     on a Pocket Outlook Application Object. Logon logs the user onto a Pocket
	     Outlook session and Logoff logs the user out.
	
	     These methods are simply called as follows:
	
	  Option Explicit
	  Dim pOLA As PocketOutlook.Application
	  Private Sub Form_Load()
	  		Set pOLA = CreateObject("PocketOutlook.Application")
	  		'Since you are going to be displaying items, you pass in the
	   
	  'form's HWND to Logon so that dialog boxes will be parented to 'this window. Otherwise, the user could go and display 'multiple items at a time.
	  		pOLA.Logon (Form1.hWnd) 'logs on to a session
	  End Sub
	  Private Sub Form_Unload(Cancel As Integer)
	   
	  		pOLA.Logoff    'logs off of a session
	  End Sub
	
	   - How to create a new contact.
	
	     1. Create a new Windows CE Project in Visual Basic.
	
	     2. Paste the following code into Form1:
	
	  Option Explicit
	  Dim pOLA As PocketOutlook.Application
	  Dim pContact As PocketOutlook.ContactItem
	  Const olCreateContact = 2
	  Private Sub Form_Load()
	  		Set pOLA = CreateObject("PocketOutlook.Application")
	  		pOLA.Logon (Form1.hWnd)
	  		AddNewContact "Maxwell", "Smart"
	  End Sub
	  Function AddNewContact(sFirstName As String, sLastName As String) As Long Set pContact = pOLA.CreateItem(olCreateContact)
	  		pContact.FirstName = sFirstName
	   
	  		pContact.LastName = sLastName
	  		pContact.Save
	  		Set pContact = Nothing
	  End Function
	  Private Sub Form_Unload(Cancel As Integer)
	  		pOLA.logoff
	  		Set pOLA = Nothing
	  End Sub
	
	   - How to view information about a contact.
	
	     Note that this sample assumes that a specific contact exists.
	     1. Create a new Windows CE Project in Visual Basic.
	
	     2. Add a command button to Form1.
	
	     3. Paste the following code into Form1:
	
	  Option Explicit
	  Dim pOLA As PocketOutlook.Application
	  Dim pContact As PocketOutlook.ContactItem
	   
	  Const olFolderContacts = 10
	  Private Sub Form_Load()
	  Set pOLA = CreateObject("PocketOutlook.Application") pOLA.Logon (Form1.hWnd)
	  End Sub
	  Private Sub Command1_Click()
	   
	  		DisplayContact "Smart, Maxwell"
	  End Sub
	  Sub DisplayContact(inpContactName As String)
	  Set pContact = pOLA.GetDefaultFolder(olFolderContacts).Items.Find( _ "[FileAs] = """ & inpContactName & """")
	   
	  Set pContact = pOLA.GetItemFromOid(pContact.oid) pContact.Display
	  		Set pContact = Nothing
	  End Sub
	  Private Sub Form_Unload(Cancel As Integer)
	  		pOLA.logoff
	  		Set pOLA = Nothing
	  End Sub
	
	   - How to obtain a list of contacts.
	     1. Create a new Windows CE Project in Visual Basic.
	
	     2. Add a list box to Form1.
	
	     3. Paste the following code into Form1:
	
	  Option Explicit
	  Dim pOLA As PocketOutlook.Application
	  Dim pContact As PocketOutlook.ContactItem
	  Dim pItems As PocketOutlook.Items
	  Const olFolderContacts = 10
	  Private Sub Form_Load()
	  Set pOLA = CreateObject("PocketOutlook.Application") pOLA.Logon (Form1.hWnd)
	  		GetContacts List1
	  End Sub
	  Private Sub GetContacts(lstCtrl As ListBox)
	  		Dim i As Integer
	   
	  		lstCtrl.Clear
	  'Add all the Contacts to a ListBox. Start by getting the
	  'Contacts folder, and then get its Item Collection.
	  		Set pItems = pOLA.GetDefaultFolder(olFolderContacts).Items
	  		For i = 1 To pItems.Count
	  				Set pContact = pItems.Item(i)
	   
	  		lstCtrl.AddItem i & ": " & pContact.FileAs Next i
	  		Set pItems = Nothing
	   
	  		Set pContact = Nothing
	  End Sub
	  Private Sub Form_Unload(Cancel As Integer) pOLA.logoff
	  		Set pOLA = Nothing
	  End Sub
	
	   - How to create an appointment.
	
	     1. Create a new Windows CE Project in Visual Basic.
	
	     2. Add a command button to Form1.
	
	     3. Paste the following code into Form1:
	
	  Option Explicit
	  Dim pOLA As PocketOutlook.Application
	  Dim pApptItem As PocketOutlook.AppointmentItem
	  Const olCreateAppointment = 1
	  Private Sub Command1_Click()
	  NewAppt "Meet with Chief", "Cone of Silence Room", _ "Discuss shoe phone repair bills", _ CDate("2/15/00 08:30:00 AM"), _ CDate("2/15/00 10:30:00 AM")
	   
	  End Sub
	  Private Sub Form_Load()
	  Set pOLA = CreateObject("PocketOutlook.Application") pOLA.Logon (Form1.hWnd)
	  End Sub
	  Private Sub NewAppt(sSubject As String, sLoc As String, _ sBody As String, dStart As Date, dEnd As Date)
	  Set pApptItem = pOLA.CreateItem(olCreateAppointment) pApptItem.Subject = sSubject
	   
	  pApptItem.Location = sLoc pApptItem.Body = sBody pApptItem.Start = dStart pApptItem.End = dEnd pApptItem.Save
	  Set pApptItem = Nothing
	  End Sub
	   
	  Private Sub Form_Unload(Cancel As Integer)
	  		pOLA.logoff
	  		Set pOLA = Nothing
	  End Sub
	
	   - How to obtain appointment information.
	     1. Create a new Windows CE Project in Visual Basic.
	
	     2. Add a command button and a list box to Form1.
	
	     3. Paste the following code into Form1:
	
	  Option Explicit
	  Dim pOLA As PocketOutlook.Application
	  Dim pApptItem As PocketOutlook.AppointmentItem
	  Dim pItems As PocketOutlook.Items
	  Const olFolderCalendar = 9
	  Private Sub Command1_Click()
	   
	  		ViewTodaysAppointments Date, List1
	  End Sub
	  Private Sub Form_Load()
	  Set pOLA = CreateObject("PocketOutlook.Application")
	  		pOLA.Logon (Form1.hWnd)
	  End Sub
	  Sub ViewTodaysAppointments(inpDate As Date, lstCtrl As ListBox) Dim iItem As Integer
	   
	  		lstCtrl.Clear
	  Set pItems = pOLA.GetDefaultFolder(olFolderCalendar).Items 'Use the Restrict method to find only those items with a start 
	  'date of today. pTodaysItems will be a new Item Collection which 'contains only those items which pass the restriction of 'occuring today.
	  Set pItems = pItems.Restrict("[Start] = """ & inpDate & """")
	  		For iItem = 1 To pItems.Count
	  				Set pApptItem = pItems.Item(iItem)
	   
	  lstCtrl.AddItem pApptItem.Subject & " at " & _ FormatDateTime(pApptItem.Start, vbShortTime)
	  		Next
	  		Set pItems = Nothing
	   
	  		Set pApptItem = Nothing
	  End Sub
	  Private Sub Form_Unload(Cancel As Integer)
	  		pOLA.logoff
	  		Set pOLA = Nothing
	  End Sub
	
	   - How to create a task.
	     1. Create a new Windows CE Project in Visual Basic.
	
	     2. Add a command button to Form1.
	
	     3. Paste the following code into Form1:
	
	  Option Explicit
	  Dim pOLA As PocketOutlook.Application
	   
	  Dim pTaskItem As PocketOutlook.TaskItem Const olCreateTasks = 3
	  Const olDialog = 1
	  Const olSound = 8
	  Private Sub Form_Load()
	  		Set pOLA = CreateObject("PocketOutlook.Application")
	  		pOLA.Logon (Form1.hWnd)
	  End Sub
	  Private Sub Command1_Click()
	  NewTask "Pick up shoe phone at repair shop", "Watch out for KAOS", _ Now() + 2, Now(), "Alarm3", True
	  End Sub
	  Sub NewTask(sSubject As String, sBody As String, _
	   
	  				dDue As Date, dStart As Date, _
	  				sSoundFile As String, bReminderSet As Boolean)
	  Set pTaskItem = pOLA.CreateItem(olCreateTasks)
	  		pTaskItem.Subject = sSubject
	   
	  pTaskItem.Body = sBody pTaskItem.DueDate = dDue pTaskItem.StartDate = dStart pTaskItem.ReminderSet = bReminderSet If bReminderSet Then 
	  pTaskItem.ReminderOptions = olSound Or olDialog pTaskItem.ReminderSoundFile = sSoundFile pTaskItem.ReminderTime = dDue - 1
	   
	  		End If
	  		pTaskItem.Save
	  		Set pTaskItem = Nothing
	  End Sub
	  Private Sub Form_Unload(Cancel As Integer) pOLA.logoff
	   
	  		Set pOLA = Nothing
	  End Sub
	
	   - How to obtain task information.
	     1. Create a new Windows CE Project in Visual Basic.
	
	     2. Add two command buttons and a list box to Form1.
	
	     3. Paste the following code into Form1:
	
	  Option Explicit
	  Dim pOLA As PocketOutlook.Application
	   
	  Dim pTaskItem As PocketOutlook.TaskItem
	  Dim pItems As PocketOutlook.Items
	  Const olFolderTasks = 13
	  Private Sub Form_Load()
	  Set pOLA = CreateObject("PocketOutlook.Application") pOLA.Logon (Form1.hWnd)
	  End Sub
	  Private Sub Command1_Click()
	   
	  		ViewTodaysTasks Date + 1, List1 End Sub
	  Private Sub Command2_Click() ViewAllTasks List1
	  End Sub
	   
	  Sub ViewTodaysTasks(inpDate As Date, lstCtrl As ListBox)
	  		Dim iItem As Integer
	  		lstCtrl.Clear
	  Set pItems = pOLA.GetDefaultFolder(olFolderTasks).Items
	  'Use the Restrict method to find only those items with a due
	  		'date of today.
	  Set pItems = pItems.Restrict("[Duedate] = """ & inpDate & """") For iItem = 1 To pItems.Count
	  				Set pTaskItem = pItems.Item(iItem)
	   
	  		lstCtrl.AddItem pTaskItem.Subject Next
	  		Set pItems = Nothing
	   
	  		Set pTaskItem = Nothing
	  End Sub
	  Sub ViewAllTasks(lstCtrl As ListBox)
	  		Dim iItem As Integer
	  		lstCtrl.Clear
	  Set pItems = pOLA.GetDefaultFolder(olFolderTasks).Items For iItem = 1 To pItems.Count
	  				Set pTaskItem = pItems.Item(iItem)
	   
	  lstCtrl.AddItem pTaskItem.Subject & " on " & _ FormatDateTime(pTaskItem.DueDate, vbShortDate)
	  		Next
	  		Set pItems = Nothing
	   
	  		Set pTaskItem = Nothing
	  End Sub
	  Private Sub Form_Unload(Cancel As Integer)
	  		pOLA.Logoff
	  		Set pOLA = Nothing
	  End Sub
	
	   - How to add a city. Cities exist in the World Clock Control Panel applet
	     and can be either userdefines or in ROM. In ROM, cities cannot be
	     modified.
	
	     When setting either the Longitude ot Latitude properties of the City
	     object, use the following standards:
	      - West is negative, East positive:
	
	        For example, 104.98 degrees W would be -10498.
	
	      - South is negative, North positive:
	
	        For example, 39.77 degrees N would be 3977.
	
	     Note that before running this code, you should close the 'World Clock'
	     Control Panel applet. Otherwise an error results.
	     1. Create a new Windows CE Project in Visual Basic.
	
	     2. Add a command button to Form1.
	
	     3. Paste the following code into Form1:
	
	  Option Explicit
	  Dim pOLA As PocketOutlook.Application
	   
	  Dim pCityItem As PocketOutlook.CityItem Dim pItems As PocketOutlook.Items
	  Const olFolderCities = 101
	   
	  Const olCreateCity = 102
	  Private Sub Form_Load()
	  Set pOLA = CreateObject("PocketOutlook.Application") pOLA.Logon (Form1.hWnd)
	  End Sub
	  Private Sub Command1_Click()
	  		AddNewCity "Steilacoom, WA", "USA"
	  End Sub
	  Private Sub AddNewCity(sCityName As String, _ sCountryName As String)
	  		'Check to see if city exists first because
	   
	  'we won't get an error if it's created twice. If CityExists(sCityName) = True Then
	  MsgBox "City already exists"
	  			Exit Sub
	  		End If
	  Set pCityItem = pOLA.CreateItem(olCreateCity) pCityItem.Name = sCityName
	   
	  		pCityItem.Country = sCountryName
	  		pCityItem.Save
	  		Set pCityItem = Nothing
	  End Sub
	  Private Function CityExists(sCityName As String) As Boolean
	  Set pItems = pOLA.GetDefaultFolder(olFolderCities).Items
	  		Set pCityItem = pItems.Find("[NAME] = """ & sCityName & """")
	  		If pCityItem Is Nothing Then
	   
	  	CityExists = False Else
	  	CityExists = True End If
	  		Set pCityItem = Nothing
	   
	  End Function
	  Private Sub Form_Unload(Cancel As Integer)
	  		pOLA.Logoff
	  		Set pOLA = Nothing
	  End Sub
	
	   - How to obtain city and time zone information.
	
	     Note that before running this code, you should close the 'World Clock'
	     Control Panel applet. Otherwise an error results.
	     1. Create a new Windows CE Project in Visual Basic.
	
	     2. Add a command button to Form1.
	
	     3. Paste the following code into Form1:
	
	  Option Explicit
	  Const olFolderCities = 101
	  Dim pOLA As PocketOutlook.Application
	   
	  Dim pCity As PocketOutlook.CityItem
	  Private Sub Form_Load()
	  Set pOLA = CreateObject("PocketOutlook.Application") pOLA.Logon (Form1.hWnd)
	  End Sub
	  Private Sub Command1_Click()
	   
	  		FindCityTimeZone "Sioux Falls, SD"
	  End Sub
	  Private Sub FindCityTimeZone(inpCity As String)
	  		Dim sTimeZone As String
	  Set pCity = pOLA.GetDefaultFolder(olFolderCities).Items.Find( _ "[NAME] = """ & inpCity & """")
	  sTimeZone = pOLA.GetTimeZoneFromIndex( _ pCity.TimezoneIndex).StandardName
	  MsgBox pCity.Name & " is in the '" & sTimeZone & "' time zone." Set pCity = Nothing
	  End Sub
	  Private Sub Form_Unload(Cancel As Integer)
	  		pOLA.Logoff
	  		Set pOLA = Nothing
	  End Sub
	
	   - How to specify a home and visiting city.
	
	     Note that before running this code, you should close the 'World Clock'
	     Control Panel applet. Otherwise an error results.
	     1. Create a new Windows CE Project in Visual Basic.
	
	     2. Add two command buttons to Form1.
	
	     3. Paste the following code into Form1:
	
	  Option Explicit
	  Const olFolderCities = 101
	  Const olHomeCity = 0
	   
	  Const olVisitingCity = 1
	  Dim pOLA As PocketOutlook.Application Dim pCity As PocketOutlook.CityItem
	  Private Sub Form_Load()
	   
	  Set pOLA = CreateObject("PocketOutlook.Application") pOLA.Logon (Form1.hWnd)
	  End Sub
	  Private Sub Command1_Click()
	   
	  		CitySetVisit "Vancouver, BC" End Sub
	  Private Sub Command2_Click() CitySetHome "Seattle, WA"
	  End Sub
	   
	  Private Sub CitySetVisit(inpCity As String)
	  Set pCity = pOLA.GetDefaultFolder(olFolderCities).Items.Find( _ "[NAME] = """ & inpCity & """")
	  		pOLA.VisitingCity = pCity
	  		pOLA.CurrentCityIndex = olVisitingCity
	  MsgBox "Visiting city is now: " & pOLA.VisitingCity.Name
	  		Set pCity = Nothing
	  End Sub
	  Private Sub CitySetHome(inpCity As String)
	  Set pCity = pOLA.GetDefaultFolder(olFolderCities).Items.Find( _ "[NAME] = """ & inpCity & """")
	  		pOLA.HomeCity = pCity
	   
	  		pOLA.CurrentCityIndex = olHomeCity
	  		MsgBox "Home city is now: " & pOLA.HomeCity.Name
	  		Set pCity = Nothing
	  End Sub
	  Private Sub Form_Unload(Cancel As Integer)
	  		pOLA.Logoff
	  		Set pOLA = Nothing
	  End Sub
	
	   - How to send items via Infrared transfer.
	
	     This sample sends a newly-created TaskItem via Infrared transfer.
	     1. Create a new Windows CE Project in Visual Basic.
	
	     2. Add a command button to Form1.
	
	     3. Paste the following code into Form1:
	
	  Dim pOLA As PocketOutlook.Application
	   
	  Dim pFolder As PocketOutlook.Folder
	  Dim pTaskItem As PocketOutlook.TaskItem Const olTaskItem = 3
	  Const olFolderInfrared = 102
	   
	  Const olCreateTasks = 3
	  Private Sub Form_Load()
	  Set pOLA = CreateObject("PocketOutlook.Application") pOLA.Logon (Form1.hWnd)
	  End Sub
	  Private Sub Command1_Click()
	   
	  		'Set up a task
	  Set pTaskItem = pOLA.CreateItem(olCreateTasks) pTaskItem.Subject = "Pick up shoe phone at repair shop" pTaskItem.StartDate = Now   'today
	   
	  pTaskItem.DueDate = Now + 1 'tomorrow pTaskItem.Save
	  		'Ship it over
	  Set pFolder = pOLA.GetDefaultFolder(olFolderInfrared) pFolder.AddItemToInfraredFolder olTaskItem, pTaskItem pFolder.SendToInfrared
	  		Set pFolder = Nothing
	   
	  		Set pTaskItem = Nothing
	  End Sub
	  Private Sub Form_Unload(Cancel As Integer)
	  		pOLA.Logoff
	  		Set pOLA = Nothing
	  End Sub
	
	   - How to receive items via Infrared transfer.
	
	     This sample receives a TaskItem sent via Infrared transfer.
	     1. Create a new Windows CE Project in Visual Basic.
	
	     2. Add a command button to Form1.
	
	     3. Paste the following code into Form1:
	
	  Option Explicit
	  Dim pOLA As PocketOutlook.Application
	   
	  Dim pFolder As PocketOutlook.Folder Dim pItems As PocketOutlook.Items 
	  Dim pTaskItem As PocketOutlook.TaskItem
	  Const olFolderTasks = 13
	  Private Sub Form_Load()
	  Set pOLA = CreateObject("PocketOutlook.Application")
	  		pOLA.Logon (Form1.hWnd)
	  End Sub
	  Private Sub Command1_Click()
	  		'Get the task from Infrared transfer
	  Set pFolder = pOLA.GetDefaultFolder(olFolderTasks)
	  		Set pItems = pFolder.ReceiveFromInfrared
	  		'Verify we got it
	  		Set pTaskItem = pItems.Item(1)
	  		MsgBox pTaskItem.Subject, vbCritical, "Task Received!"
	  		Set pFolder = Nothing
	   
	  Set pItems = Nothing
	  		Set pTaskItem = Nothing End Sub
	   
	  Private Sub Form_Unload(Cancel As Integer)
	  		pOLA.Logoff
	  		Set pOLA = Nothing
	  End Sub
	
	REFERENCES
	==========
	
	"Pocket Outlook Object Model.doc", which is included with the POOM SDK download.
	
	Additional query words: vbce vbce6 wce
	
	======================================================================
	Keywords          : kbOutlook kbToolkit kbVBp600 kbOSWinCEsearch kbGrpDSVB 
	Technology        : kbVBSearch kbOutlookSearch kbAudDeveloper kbOSWinCE kbPocketSearch kbPocketOutlookSearch kbWinCETKVBSearch kbWinCESearch kbPocketOutlook301
	Version           : :3.01
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
