---
layout: page
title: "Q161118: XCLN: Troubleshooting POP3 Connections to Exchange Server"
permalink: /kb/161/Q161118/
---

## Q161118: XCLN: Troubleshooting POP3 Connections to Exchange Server

{% raw %}

	Article: Q161118
	Product(s): Microsoft Exchange
	Version(s): winnt:5.0
	Operating System(s): 
	Keyword(s): kbtool
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article lists steps to help you troubleshoot problems when you attempt to
	connect to the Internet Mail Server from an e-mail client using post office
	protocol version 3 (POP3). These steps are based on information in the Request
	for Comments (RFC) 1725 and RFC 1939 specifications.
	
	MORE INFORMATION
	================
	
	Basic Troubleshooting
	---------------------
	
	If you are unable to connect to the Internet Mail Server from an e-mail client
	using POP3, use the following steps to troubleshoot the problem. After
	performing each step, check to see if the issue has been resolved.
	
	1. Verify that the e-mail client is POP3-compliant. Many e-mail clients are not
	  POP3-compliant. In particular, many newer e-mail clients support Internet
	  Mail Access Protocol version 4 (IMAP4). Microsoft Exchange Server versions
	  4.0 and 5.0 do not support IMAP4. For IMAP4 support you must upgrade to
	  Microsoft Exchange Server version 5.5. Microsoft Exchange Server supports
	  POP3 as defined in the RFC 1725, RFC 1734, RFC 1939, and RFC 1953
	  specifications.
	
	2. Use the Telnet tool to connect to the Microsoft Exchange Server. To do so,
	  follow these steps:
	
	  a. On the e-mail client, start Telnet. For the host name, type the name of
	     the Microsoft Exchange Server computer, and for the port type, type 110.
	     If a "term type" is requested, do not type anything. For example, type the
	     following command to start Telnet:
	
	  telnet <server> 110
	
	     where <server> is the name of the Microsoft Exchange Server computer.
	     If you are running Windows 95, Windows NT Workstation, or Windows NT
	     Server, you can type the above command at a command prompt or in the Run
	     dialog box. If you are running Windows NT Workstation or Windows NT Server
	     version 3.51, you can open the Run dialog box from the File menu or the
	     task list.
	
	     When you type the above command and then press ENTER, a message similar to
	     the following should be displayed:
	
	  +OK Microsoft Exchange POP3 server version 5.0.1457.10 ready
	
	     NOTE: The version number might be different, but it should be 5.0.1457.10
	     or later.
	
	  b. Enable local echo for the current Telnet session. To do so, on the
	     Terminal menu, click Preferences, click the Local Echo check box to select
	     it, and then click OK.
	
	  c. Type the following command, and then press ENTER: user
	     <domain>\<username>\<mailbox> where <domain> is
	     the name of the domain in which the user's account is located,
	     <username> is the user name, and <mailbox> is the user's
	     mailbox. Note that the <mailbox> portion of the above command is
	     only necessary if it is different from the <username> portion. When
	     you press ENTER, "+OK" (without quotation marks) should be displayed.
	
	  d. Type the following command, and then press ENTER:
	
	  pass <password>
	
	     where <password> is the user's password. When you press ENTER, the
	     following message should be displayed:
	
	  +OK User successfully logged on
	
	  e. To determine if the user has new messages, type "stat" (without quotation
	     marks), and then press ENTER. After you press ENTER, the following message
	     should be displayed:
	
	  +OK <x><yyyy>
	
	     where <x> is the number of new messages and <yyyy> is the total
	     size of the messages in bytes. This is known as a "drop listing."
	
	  f. To end the Telnet session, type "quit" (without quotation marks), and then
	     press ENTER. When you press ENTER, a message similar to the following
	     should be displayed:
	
	  +OK Microsoft Exchange POP3 server version 5.0.1457.10 signing off
	
	NOTE: The above POP3 commands can only be used to troubleshoot problems when you
	attempt to receive messages. A POP3 client uses Simple Mail Transfer Protocol
	(SMTP) to send messages. For information about how troubleshoot problems when
	you attempt to send messages, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q153119 XFOR: Telnet to Port 25 of IMC to Test IMC Communication
	
	Additional Troubleshooting
	--------------------------
	
	If the problem still occurs, perform these steps. After performing each step,
	check to see if the issue has been resolved.
	
	1. Verify that the POP3 protocol is enabled for the site Protocols container and
	  the Protocols container on the server.
	
	2. Verify that POP3 support is not disabled for the user's mailbox.
	
	3. Verify that the client can ping the server using the server's Internet
	  protocol (IP) address and the server's computer name.
	
	4. Run the Rpings.exe tool that is located on the Microsoft Exchange Server
	  CD-ROM. Rpings.exe runs on the server; a client program must also be run on
	  the client. If you are running Windows or Windows for Workgroups version 3.x,
	  run Rpingc16.exe on the client. If you are running Windows 95, Windows NT
	  Server, or Windows NT Workstation, run Rpingc32.exe on the client.
	
	  NOTE: The Rpings.exe tool is used to determine if the client can connect to
	  the server using remote procedure call (RPC). POP3 clients do not connect to
	  the Microsoft Exchange Server computer using RPC.
	
	5. Try to use the Microsoft Exchange Windows NT client to connect to the server
	  from the same computer on which Microsoft Exchange Server is installed.
	
	6. Try using a different e-mail client. For example, use Microsoft Outlook with
	  the Internet Mail information service in the client profile or use Microsoft
	  Outlook Express.
	
	7. Verify that the Private information store database is consistent and not
	  corrupt. This can cause POP3 login's to fail and POP3 sessions to hang after
	  a command has been issued.
	
	
	If the problem still occurs, contact the manufacturer of the e-mail client for
	additional assistance.
	
	For additional information, please see the following articles in the Microsoft
	Knowledge Base:
	
	  Q161116 XCLN: POP3 Supported Command Set for Exchange Server 5.0
	
	  Q155048 XCLN: Troubleshooting Startup of Windows Client Using TCP/IP
	
	  Q153119 XFOR: Telnet to Port 25 of IMC to Test IMC Communication
	
	Additional query words: ims imc
	
	======================================================================
	Keywords          : kbtool 
	Technology        : kbExchangeSearch kbExchange500 kbZNotKeyword2
	Version           : winnt:5.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
