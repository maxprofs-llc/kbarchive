---
layout: page
title: "Q194400: FP98: Command-Line Arguments for Server Administrator"
permalink: /kb/194/Q194400/
---

## Q194400: FP98: Command-Line Arguments for Server Administrator

{% raw %}

	Article: Q194400
	Product(s): Word Front Page
	Version(s): WINDOWS:
	Operating System(s): 
	Keyword(s): kbdta
	Last Modified: 03-OCT-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft FrontPage 98 for Windows 
	-------------------------------------------------------------------------------
	
	For a Microsoft FrontPage 2000 version of this article, see Q247864.
	
	For a Microsoft FrontPage 97 version of this article, see Q164584.
	
	SUMMARY
	=======
	
	FrontPage Server Administrator is available in two forms:
	
	- The first form is Fpsrvwin.exe, which is a Windows application.
	
	  -and-
	
	- The second form is Fpsrvadm.exe, which is a command-line only version of the
	  server administrator.
	
	To view the command-line options for Fpsrvadm.exe, point to Programs on the
	Windows Start menu, and then click MS-DOS prompt. At the MS-DOS prompt, go to
	the \Program Files\Microsoft FrontPage\Bin folder, and then type the following:
	
	  " Fpsrvadm -h " (without the quotation marks)
	
	This article describes the command-line arguments available to both forms of the
	FrontPage Server Administrator.
	
	MORE INFORMATION
	================
	
	Fpsrvadm.exe
	------------
	
	Fpsrvadm.exe is an MS-DOS and UNIX application, which supports the following
	command-line arguments:
	
	Usage: fpsrvadm [-help]
	               [-operation <install | upgrade | uninstall | check |
	                 security |enable | disable | recalc | putfile |
	                 recalcfile>]
	               [-port <nnnn>]
	               [-web <web name>]
	               [-root <frontpage root directory>]
	               [-type <ncsa | ncsa-manual-restart
	                       | apache | apache-manual-restart
	                       | cern | cern-manual-restart
	                       | netscape | netscape-manual-restart>]
	               [-servconf <server config file>]
	               [-multihost <hostname>]
	               [-username <username>]
	               [-password <password>]
	               [-ipaddress <IP address>]
	               [-destination <destination Url>]
	               [-filename <file name>]
	
	               [-xUser <UNIX username>]
	               [-xGroup <UNIX group>]
	               [-noChownContent Yes]
	
	You can shorten the command-line arguments by using the first letter of each
	command, with the exception of Password, which uses "-pw", xUser, which uses
	"-xu", and xGroup, which uses "-xg".
	
	Examples of command-line arguments for Fpsrvadm.exe
	---------------------------------------------------
	
	  fpsrvadm -o install -r "c:\Program Files\Microsoft FrontPage"
	           -t frontpage  -u user -pw password
	           -s "c:\FrontPage Webs\server\conf\httpd.cnf" -m ""
	  fpsrvadm -o install -p 80 -w webname (sub web)
	  fpsrvadm -o upgrade -p 80
	  fpsrvadm -o uninstall -p 80
	  fpsrvadm -o check -p 80
	  fpsrvadm -o check -p all
	  fpsrvadm -o disable -p 80
	  fpsrvadm -o security -p 80 -w webname -u username -pw password
	           -i ipaddress
	  fpsrvadm -o recalc -p 80 -w webname
	  fpsrvadm -o putfile -p 80 -w webname -d url -f filename
	  fpsrvadm -o recalcfile -p 80 -w webname -d url
	
	If Fpsrvadm needs additional information, you will be prompted to enter this
	information at the MS-DOS prompt.
	
	NOTE: The following server types are not documented in the Fpsrvadm Help file.
	The FrontPage Server Administrator retrieves these server types from DLLs
	installed on the server system when you install the FrontPage Server
	Extensions:
	
	  Microsoft Internet Information Server      msiis
	  Microsoft Personal Web Server              msiis
	  Microsoft Peer Web Services                msiis
	  O'Reilly & Associates WebSite              website
	  Netscape Commerce                          netscape-commerce
	  Netscape Communications                    netscape-communications
	  Netscape FastTrack                         netscape-fasttrack
	  Netscape Enterprise                        netscape-enterprise
	  FrontPage Personal Web Server              frontpage
	
	Of the supported Web servers on Windows NT or Windows 95 operating systems, the
	only servers that require configuration files are Netscape and the FrontPage
	Personal Web Server. When you install extensions with Fpsrvadm or Fpsrvwin to
	other servers on these operating systems, you may omit the configuration file
	option.
	
	Paths that contain spaces must be enclosed within quotation marks (""). For
	example, assuming FrontPage is installed in the c:\Microsoft FrontPage folder,
	the following command will fail:
	
	  fpsrvadm -r c:\microsoft frontpage
	
	but this command will not fail:
	
	  fpsrvadm -r "c:\microsoft frontpage"
	
	The destination and filename arguments are only used with the putfile and
	recalcfile options. These arguments are used when you place content into a
	FrontPage Web without using FrontPage Explorer. The filename argument accepts
	the name of the file you want to place into the Web. The destination file
	accepts the destination URL or the Web for which you want to recalculate links.
	
	The recalcfile option recalculates the Web links going to or from a given file.
	You can use this as a substitute for recalculating an entire Web if only one or
	a few files have changed. The putfile option places a file into a FrontPage Web
	using Fpsrvadm.
	
	The ipaddress argument limits access to the web server based on the IP address.
	This feature of FrontPage Server Administrator is not available on Microsoft
	Internet Information Servers (IIS).
	
	Fpsrvwin.exe
	------------
	
	
	Fpsrvwin.exe takes only a subset of the arguments available to Fpsrvadm.exe. The
	reason is that Fpsrvwin functionality was intended to support the setup program.
	Microsoft recommends using Fpsrvadm for batch mode server administrator
	operation. Future versions of Fpsrvwin may not support command-line arguments.
	
	Fpsrvwin command-line functionality only supports install, upgrade, and uninstall
	because these are the operations necessary from FrontPage setup. The command
	line options for Fpsrvwin.exe are:
	
	  -o   -operation <install | upgrade | uninstall>
	  -p   -port <nnnn>
	  -m   -multihost <hostname>
	  -ma   -multihost-all
	  -w   -webname <web name>
	  -t   -type <frontpage | microsoft | website | netscape |
	          netscape-enterprise ...>
	  -s   -servconf
	
	If Fpsrvwin needs additional information not provided by its command-line
	options, it will prompt you for the information.
	
	Additional query words: fp98
	
	======================================================================
	Keywords          : kbdta 
	Technology        : kbFrontPageSearch _IKkbZNotKeyword4 kbFrontPage98Search kbZNotKeyword3
	Version           : WINDOWS:
	Hardware          : x86
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
