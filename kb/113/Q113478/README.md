---
layout: page
title: "Q113478: README.TXT: Workgroup Add-On for MS-DOS 3.11"
permalink: /kb/113/Q113478/
---

## Q113478: README.TXT: Workgroup Add-On for MS-DOS 3.11

{% raw %}

	Article: Q113478
	Product(s): Microsoft Access Distribution Kit
	Version(s): MS-DOS:3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 18-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Workgroup Add-On for MS-DOS, version 3.11 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The following information is contained in the Microsoft Workgroup Add-On for
	MS-DOS README.TXT file.
	
	Additional Notes About Microsoft Workgroup Add-On for MS-DOS and Mail
	---------------------------------------------------------------------
	
	This document contains information about Microsoft(R) Workgroup Add-On
	for MS-DOS(R) and Mail that wasn't available when the "Workgroup
	Add-On for MS-DOS User's Guide" was printed.
	
	1. Notes About Workgroup Add-On for MS-DOS
	  1.1  Stop the Server Before Shutting Down Your Computer
	  1.2  If You Have an 8088 Processor
	  1.3  Setup Requires 429K Available Memory
	  1.4  Setup is Slow on Some Computers
	  1.5  Using Workgroup Add-On with Novell NetWare
	  1.6  Connecting to Novell NetWare Servers and Computers Running
	       Workgroup Add-On
	  1.7  Direct Hosting over IPX
	  1.8  Installing Remote Access Service 1.1
	  1.9  Using TSRs with Workgroup Add-On
	  1.10 Using Qualitas Maximize or Quarterdeck Optimize
	  1.11 Workgroup Add-On Cannot Be Set Up on DoubleDisk Drive
	  1.12 Making the Pop-up Interface Visible on a Monochrome Monitor
	  1.13 Using QEMM Lastdrive
	  1.14 If Your COMMAND.COM File is Not in Root Directory
	  1.15 Enabling Validated Logons to Windows NT and LAN Manager
	       Domains
	  1.16 Network Settings in SYSTEM.INI
	  1.17 Network Settings in CONFIG.SYS
	  1.18 Using CHKDSK, SCANDISK, and DEFRAG with Workgroup Add-On
	  1.19 Using INTERLNK and INTERSVR
	  1.20 Browsing the Network Requires a Windows for Workgroups or
	       Windows NT Computer on the Network
	  1.21 Viewing Workgroup Add-On Server from Workgroup Connection 1.0,
	       LAN Manager 2.X, or Windows NT
	  1.22 Sharing Not Supported for Serial Printers and Communications
	       Devices
	
	2. Notes About Mail
	  2.1 Messages on Main Screen or in Private Folders Can't Be
	      Compressed
	  2.2 Using Micro with MS-DOS Shell
	  2.3 Using Micro with Graphics-Mode Applications
	  2.4 Removing the Mail Notifier
	
	1. Notes About Workgroup Add-On for MS-DOS
	==========================================
	
	1.1 Stop the Server Before Shutting Down Your Computer
	------------------------------------------------------
	You should stop the server with the NET STOP SERVER command prior to
	rebooting or turning off your computer. If the server is running, and
	there are people using shared resources, the shared data may get
	corrupted when the computer is shut down.
	
	1.2 If You Have an 8088 Processor
	---------------------------------
	You must use the basic redirector if your computer has an 8088
	processor. The basic redirector is the default.
	
	1.3 Setup Requires 429K Available Memory
	----------------------------------------
	In order to run Workgroup Add-On for MS-DOS Setup, you must have 429K
	of available conventional memory.
	
	1.4 Setup is Slow on Some Computers
	-----------------------------------
	On some computers, particularly those with 8088 processors, Workgroup
	Add-On for MS-DOS Setup may appear to pause for as long as five
	minutes. Do not restart your computer.
	
	1.5 Using Workgroup Add-On with Novell NetWare
	----------------------------------------------
	If you have Novell(R) NetWare(R) installed when you set up Workgroup
	Add-On, your computer will be automatically set up so you can continue
	to use the NetWare server.
	
	1.6 Connecting to Novell NetWare Servers and Computers Running
	   Workgroup Add-On
	--------------------------------------------------------------
	If you have Novell NetWare installed, you can set up your computer
	to be able to connect to NetWare servers and to computers running
	Workgroup Add-On. Follow these steps:
	
	1. Verify that your computer has the Novell ODI MLID driver loaded
	  rather than the IPX monolithic/dedicated IPX.COM driver.
	
	2. Have available a disk containing the Novell ODINSUP.COM file.
	
	3. During Workgroup Add-On Setup, select ODI/NDIS Support Driver
	  from the list of adapters, and insert the disk containing
	  ODINSUP.COM as requested.
	
	4. This step describes how to configure your NET.CFG file to work
	  with ODINSUP.COM. If you need additional information, see the
	  ODINSUP.DOC file provided by Novell.
	
	  If you have only one ODI MLID driver, and if you have all the
	  frames enabled for that driver, the only modification you
	  need to make to the NET.CFG file is:
	
	       Protocol ODINSUP
	           BUFFERED
	
	  The BUFFERED parameter enables you to use the Microsoft NetBEUI
	  protocol.
	
	  If you have more than one ODI MLID driver, you need to add the
	  following information to NET.CFG. Note that ODINSUP can be
	  bound to a maximum of four ODI MLID drivers.
	
	       Protocol ODINSUP
	           BUFFERED
	           BIND <ODI MLID driver1>
	           BIND <ODI MLID driver2>
	
	  If you do not have all the frames enabled, add the following
	  frames to the Link Driver <ODI MLID driver> section of NET.CFG.
	
	       Frame Ethernet_802.3
	       Frame Ethernet_II
	       Frame Ethernet_802.2
	       Frame Ethernet_SNAP
	
	  A NET.CFG file for an Intel EtherExpress 16 card should include
	  the following:
	
	       Link Driver EXP16ODI
	         Frame Ethernet_802.3
	         Frame Ethernet_II
	         Frame Ethernet_802.2
	         Frame Ethernet_SNAP
	         INT   10
	         PORT  300
	
	       Protocol ODINSUP
	           BUFFERED
	
	5. Workgroup Add-On Setup adds the following lines to your
	  AUTOEXEC.BAT file.
	
	       NET INIT
	       ODINSUP.COM
	       NET START
	
	  Verify that these lines appear at the end of your AUTOEXEC.BAT
	  file. If the Workgroup Add-On and ODINSUP directories are not in
	  your search path, add a drive and path to each line.
	
	1.7 Direct Hosting over IPX
	---------------------------
	If you have IPX loaded, you may direct host over IPX by selecting the
	IPX/SPX Support Driver from the list of adapters.
	
	1.8 Installing Remote Access Service 1.1
	----------------------------------------
	Use the Workgroup Add-On setup program, rather than the setup program
	provided with RAS 1.1.
	
	1. In the Workgroup Add-On directory, run SETUP.EXE.
	
	2. Choose Change Network Settings, and then select Add Adapter.
	
	3. Select Microsoft Remote Network Access Driver from the list of
	  adapters, and then choose The Listed Options Are Correct.
	
	4. After running Setup, run the RASCOPY.BAT batch file. It will prompt
	  you for disk 1 and disk 2.
	
	To disable remote access, remove Microsoft Remote Network Access
	Driver from the list of adapters. To re-enable it, follow steps 1
	through 3.
	
	When the Remote Access files are installed, a RAS directory is created
	in your Workgroup Add-On directory. Use the SETUP.EXE program in this
	directory only to configure your modem, not to configure network
	settings. In particular, do not select Enable Remote Access or Remove
	Remote Access when running SETUP.EXE from the RAS directory.
	
	1.9 Using TSRs with Workgroup Add-On
	------------------------------------
	If you start any terminate-and-stay-resident programs (TSRs) and you
	are using the basic redirector, you might be unable to unload the
	basic redirector.
	
	1.10 Using Qualitas Maximize or Quarterdeck Optimize
	----------------------------------------------------
	In some rare situations, Qualitas(R) Maximize and Quarterdeck(R)
	Optimize may attempt to load some Workgroup Add-On for MS-DOS
	commands into the upper memory area. If this causes problems, use
	Maximize or Optimize in manual mode and do not use it to load
	Workgroup Add-On commands into the upper memory area. Workgroup
	Add-On automatically loads its commands into the upper memory area,
	if there is enough space. For information about using manual mode,
	see your Maximize or Optimize documentation.
	
	1.11 Workgroup Add-On Cannot Be Set Up on DoubleDisk Drive
	----------------------------------------------------------
	You cannot use Workgroup Add-On for MS-DOS on a Vertisoft Systems
	DoubleDisk drive. You must set up Workgroup Add-On on another type of
	drive.
	
	1.12 Making the Pop-up Interface Visible on a Monochrome Monitor
	----------------------------------------------------------------
	To make the Workgroup Add-On for MS-DOS pop-up interface appear
	in monochrome mode, type MODE MONO at the MS-DOS command prompt before
	you display the pop-up interface, or include the MODE MONO command in
	your AUTOEXEC.BAT file.
	
	1.13 Using QEMM Lastdrive
	-------------------------
	If you add drive letters by using QEMM(R) Lastdrive, and then use
	Workgroup Add-On for MS-DOS to connect to one of them, the connection
	will be successful but no information about the shared resources on
	it will be displayed.
	
	1.14 If COMMAND.COM is Not in Root Directory
	--------------------------------------------
	Workgroup Add-On for MS-DOS will not start if your COMMAND.COM file is
	not in the root directory of your startup drive, unless you have a
	SHELL command in your CONFIG.SYS file that specifies the location of
	COMMAND.COM. For information about the COMMAND and SHELL commands,
	see your MS-DOS documentation.
	
	1.15 Enabling Validated Logons to Windows NT and LAN Manager Domains
	--------------------------------------------------------------------
	You must run the Workgroup Add-On for MS-DOS full redirector to have
	your user name and password validated by a Microsoft Windows NT(TM)
	or
	LAN Manager server.
	
	1.16 Network Settings in SYSTEM.INI
	-----------------------------------
	There are four settings in the [Network] section of your SYSTEM.INI
	file that apply to Workgroup Add-On for MS-DOS.
	
	 MaxShares=
	    Determines the maximum number of resources that you can share
	    from this computer. This number cannot be increased when the
	    server is running. To increase this number, stop the server by
	    using the NET STOP SERVER command, change the setting, and then
	    restart the server by using the NET START SERVER command. The
	    default value is 3. The maximum is 10.
	
	 MaxConnections=
	    Determines the maximum number of users that can connect to the
	    server at any point in time. Like the MaxShares setting, you must
	    stop and restart the server to increase the number. The default
	    value is 8.
	
	 ComputerName=
	    The name of your computer.
	
	 AutoStart=
	    If you choose a network adapter during setup, and specify the
	    startup option Run Workgroup Add-On Logon, AutoStart shows which
	    redirector you are using. If you select No Network Adapter from
	    the adapter list, or Do Not Run Workgroup Add-On from the startup
	    options, AutoStart has no value, but the NET START command still
	    appears in your AUTOEXEC.BAT file.
	
	1.17 Network Settings in CONFIG.SYS
	-----------------------------------
	There are two settings in your CONFIG.SYS file that apply to Workgroup
	Add-On for MS-DOS.
	
	 Files=
	    Determines the maximum number of files that can be open on the
	    server at a given time. The default value is 30.
	
	 INSTALL=[[drive:]path]SHARE.EXE [/F:space] [/L:locks]
	    Starts the Share program, which installs file-sharing and locking
	    capabilities, for your disks and network drives. If you are
	    sharing multiple files or printers, you may need to increase the
	    value of the /F and /L parameters.
	
	    /F:space allocates file space (in bytes) for the MS-DOS storage
	    area used to record file-sharing information. The default value
	    is 2048. Each open file requires enough space for the length of
	    the full path and filename.
	
	    /L:locks sets the number of files that can be locked at one time.
	    The default value is 20.
	
	1.18 Using CHKDSK, SCANDISK, and DEFRAG with Workgroup Add-On
	-------------------------------------------------------------
	To use the MS-DOS CHKDSK, SCANDISK, and DEFRAG commands, you must
	first stop the server by typing NET STOP SERVER.
	
	1.19 Using INTERLNK and INTERSVR
	--------------------------------
	Do not use the MS-DOS INTERLNK or INTERSVR commands with Workgroup
	Add-On for MS-DOS.
	
	1.20 Browsing the Network Requires a Windows for Workgroups or
	    Windows NT Computer on the Network
	---------------------------------------------------------------
	Workgroup Add-On for MS-DOS does not provide a browse master.  In
	order for you to browse the network, a browse master must be present.
	Therefore, a computer running Windows for Workgroups or Windows NT
	must be on the network and belong to the same workgroup as the
	computer running Workgroup Add-On for MS-DOS.
	
	If the Windows for Workgroups or Windows NT computer is not present or
	doesn't belong to your workgroup, when you type NET VIEW an error
	message appears, stating that the list of servers for the workgroup
	is not available. If you are using the pop-up interface, no servers
	will be displayed in the Browse box.
	
	Note that this does not prevent you from connecting to a shared
	resource. You will just need to know the name of the server and share
	beforehand in order to connect to it.
	
	The MaintainServerList switch specifies whether a Windows for
	Workgroups computer can act as a browse master.  This switch would
	appear in the [network] section of the Windows for Workgroups
	SYSTEM.INI file. If this switch is not present, the default for
	MaintainServerList is Auto; that is, the Windows for Workgroups
	computer will automatically become a browse master after it detects
	that none are available in its workgroup.
	
	If you want your Windows for Workgroups computer to always be the
	browse master, add the line MaintainServerList=Yes to the [network]
	section of the Windows for Workgroups SYSTEM.INI file.
	
	1.21 Viewing Workgroup Add-On Server from Workgroup Connection 1.0,
	    LAN Manager 2.X, or Windows NT
	-------------------------------------------------------------------
	You will not be able to view the shared resources on a Workgroup
	Add-On for MS-DOS server from a computer running Workgroup Connection
	1.0, LAN Manager 2.X or Windows NT. You will, however, be able to
	connect to the shared resources.
	
	1.22 Sharing Not Supported for Serial Printers and Communications
	-----------------------------------------------------------------
	You can share your printer if it is connected to a parallel port
	(LPT), but not if it is connected to a serial (COM) port.  You also
	cannot share your communications devices.
	
	2. Notes About Mail
	===================
	
	2.1 Messages on Main Screen or in Private Folders Cannot Be Compressed
	----------------------------------------------------------------------
	The person who administers your workgroup post office can compress
	only the shared folders stored on it.
	
	2.2 Using Micro with MS-DOS Shell
	---------------------------------
	Micro does not operate correctly if you start it after you start
	MS-DOS Shell. To use Micro with MS-DOS Shell, start Micro, and then
	start MS-DOS Shell.
	
	2.3 Using Micro with Graphics-Mode Applications
	-----------------------------------------------
	If you use programs, including MS-DOS Shell, that switch your monitor
	into graphics mode, start Micro with the -F option.
	
	2.4 Removing the Mail Notifier
	------------------------------
	If you start Micro with the -F option, a notifier or flag appears on
	your screen when you receive a new mail message. To remove the
	notifier from your screen, press ALT+F1, or switch to the Mail
	program.
	
	Additional query words: 3.11 wfwg dos wfw wgao
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbWFWSearch kbWFW311DOS
	Version           : MS-DOS:3.11
	
	=============================================================================
	

{% endraw %}
