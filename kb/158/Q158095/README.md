---
layout: page
title: "Q158095: XCLN: Using ShivaRemote with Exchange (Win 3.x/LanMan NetBEUI)"
permalink: /kb/158/Q158095/
---

## Q158095: XCLN: Using ShivaRemote with Exchange (Win 3.x/LanMan NetBEUI)

{% raw %}

	Article: Q158095
	Product(s): Microsoft Exchange
	Version(s): WINDOWS:4.0,5.0
	Operating System(s): 
	Keyword(s): kbenv kbsetup kbusage
	Last Modified: 09-APR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Windows 3.x client, versions 4.0, 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	A white paper on ShivaRemote is located on Microsoft TechNet and can also be
	found on the following World Wide Web location:
	
	  http://www.microsoft.com/ExchangeSupport/
	
	ShivaRemote 3.59 can be used with the Microsoft Exchange client to allow users to
	remotely access a computer running Microsoft Exchange Server (either through a
	computer running Windows NT Server with RAS or Shiva LanRover). This article
	shows you how to install and configure the ShivaRemote software that ships with
	Microsoft Exchange to work over LanMan NetBEUI version 2.2c.
	
	(For information about setting up Shiva for use over other protocols, see the
	Reference section below).
	
	MORE INFORMATION
	================
	
	To configure your computer so that you can use ShivaRemote:
	
	1. Install MS-DOS on your computer.
	
	2. Install Microsoft LAN Manager 2.2 Full Redirector (LanMan software is located
	  on the Windows NT 3.51 Server compact disc in the Clients\Lanman\disks
	  directory).
	
	3. Install Microsoft Windows 3.1.
	
	4. Install Microsoft Exchange Windows 3.x client.
	
	5. Run the ShivaRemote Setup program from the Microsoft Exchange program group.
	
	6. When ShivaRemote Setup is complete, restart your computer so that the
	  configuration changes you made take effect.
	
	7. After your computer restarts, make the following changes to Config.sys and
	  Protocol.ini:
	
	  Config.sys:
	
	      DEVICE=C:\SHIVA\DIALNDIS.EXE    <- Add this line.
	
	  Protocol.ini:
	
	  NOTE: The name of the NETBEUI section below may vary. The "T1" entry specifies
	  the main NETBEUI time-out value; 8000 specifies 8 seconds.
	
	      [NETBEUI]
	      ; BINDINGS = "UBNEITP_NIF"      <- Make this line a comment.
	      BINDINGS=SDIALIN$               <- Add this line.
	      T1=8000                         <- Add this line.
	      [SDIALIN$]                      <- Add this line.
	      DriverName=SDIALIN$             <- Add this line.
	
	8. Your computer should be configured for ShivaRemote dial-in. Restart your
	  computer again, and watch for error messages as the computer starts.
	
	9. You must log on to the network before starting the Microsoft Exchange client.
	  If you are not connected to the network when you log on to the network, LAN
	  Manager will display the following message:
	
	  You are logged on, but have not been validated by a server. Therefore, you
	  may not have permission to use some network resources.
	
	10. Click OK and proceed.
	
	You can configure LAN Manager to prompt you to log on to the network when you
	start Windows.
	
	To configure LAN Manager, use one of the following methods:
	
	- Configure LAN Manager using the Setup program, as follows:
	
	  1. Run the LAN Manager Setup program (Setup.exe) in your LAN Manager
	     directory (C:\Lanman.dos).
	
	  2. On the Configuration menu, click Workstation Settings.
	
	  3. In the Workstation Settings dialog box, click OK.
	
	  4. In the Support For Windows Environment dialog box, click Yes and click OK.
	
	  5. In the Windows Directory dialog box, type the directory where Windows is
	     installed (by default C:\Windows) and click OK.
	
	  6. In the Memory Management dialog box, choose your memory management
	     settings and click OK.
	
	  7. On the LAN Manager menu, click Exit Setup.
	
	  8. Restart your computer.
	
	  -OR-
	
	- Add the following commands to your Autoexec.bat file (or type the commands at
	  the MS-DOS prompt):
	
	  net start workstation
	  load networking_protocols
	  net logon username
	
	  Once you have the above setup, restart and ensure you receive no error
	  messages when booting with the newly configured Autoexec.bat and Config.sys.
	
	To install the client:
	
	1. Install the Microsoft Exchange Windows 3.x client software (run Setup from
	  the Microsoft Exchange Windows 3.x client compact disc or from a sharepoint).
	  Select Custom install and verify that Shiva is selected. (Setup will create a
	  "ShivaRemote setup" icon in the Microsoft Exchange Program group).
	
	2. If possible, verify a valid Exchange mailbox/account exists while connected
	  to the LAN. (Start the Microsoft Exchange client, create a profile and make
	  sure you can log on to your mailbox and send a piece of mail to yourself).
	
	To install ShivaRemote:
	
	1. Run "ShivaRemote setup" from the Microsoft Exchange Program group.
	
	2. Click OK to Install ShivaRemote.
	
	3. Select the port and your specific modem manufacturer/model.
	
	4. Specify a Description, Dial-in-Name (NT account that has been granted dial-in
	  access on the server), Password (Password for the NT Account you are dialing
	  in on), and Phone number.
	
	To connect to the computer running Microsoft Exchange Server:
	
	1. Dial the computer running RAS. (Microsoft Exchange is supported dialing into
	  either a computer running Windows NT Server with RAS or a Shiva LanRover.)
	
	2. Once connected, minimize ShivaRemote Connect
	
	3. Start the Microsoft Exchange Windows 3.x client (online, as a test). Type the
	  User Name (Exchange Mailbox Name), the Password (Windows NT Domain Password),
	  and the Domain (Windows NT Domain Name that your account is in) and verify
	  you can be properly logged on.
	
	  If the above step allows you to properly send/receive mail, Shiva and
	  Microsoft Exchange are configured correctly.
	
	The Microsoft Exchange client remote capabilities can now be configured (remote
	mail or off-line folders).
	
	To setup the Microsoft Exchange client to automatically dial while working
	offline :
	
	1. In Control Panel/Mail-Fax, select the properties for Exchange Server in the
	  profile and on the "dial up networking" tab
	
	2. Select the Shiva connection name that was tested in step 1 under "dial using
	  the following connection."
	
	3. Type the user name, password, and domain name in the dialog box.
	
	You can start the Microsoft Exchange client offline and select either the "remote
	mail/connect" or "sync this folder" check box. Shiva will dial and transmit
	necessary information (depending on whether off-line folders [.ost files] or
	.pst files are being used).
	
	REFERENCES
	==========
	
	Updated modem scripts for use with ShivaRemote can be found on Shiva's web page
	at www.shiva.com under "support"/modem scripts.
	
	Additional configuration information may also be found in the config.hlp file
	installed during installation of the ShivaRemote software.
	
	For more information about specific remote options with the Microsoft Exchange
	Windows 3.x client, see the following article in the Microsoft Knowledge Base :
	
	  Q139934 XCLN: The Microsoft Exchange Client and Mobile Users
	
	The following articles in the Microsoft Knowledge Base describe additional
	supported Shiva configurations for use with Microsoft Exchange Server:
	
	  Q158124 XCLN: ShivaRemote with Exchange - RAS Server Considerations
	
	  Q158074 XCLN: Using ShivaRemote with Exchange (DOS/real-mode IPX)
	
	  Q157740 XCLN: Using ShivaRemote with Exchange (DOS/LanMan TCP/IP)
	
	  Q158077 Using ShivaRemote with Exchange (Windows 3.x/real-mode IPX)
	
	  Q158111 XCLN: ShivaRemote with Exchange (WFW 3.11/WFW TCP/IP or NetBEUI)
	
	The third-party contact information included in this article is provided to help
	you find the technical support you need. This contact information is subject to
	change without notice. Microsoft in no way guarantees the accuracy of this
	third-party contact information.
	
	
	Additional query words: remote mail
	
	======================================================================
	Keywords          : kbenv kbsetup kbusage 
	Technology        : kbExchangeSearch kbExchange500 kbExchange400 kbExchangeClientSearch kbZNotKeyword3
	Version           : WINDOWS:4.0,5.0
	
	=============================================================================
	

{% endraw %}
