---
layout: page
title: "Q266115: Resources for Installing and Using IIS 5.0"
permalink: /kb/266/Q266115/
---

## Q266115: Resources for Installing and Using IIS 5.0

{% raw %}

	Article: Q266115
	Product(s): Internet Information Server
	Version(s): 5.0
	Operating System(s): 
	Keyword(s): kbOSWin2000
	Last Modified: 20-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Services version 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article provides information and additional resources for the following
	subjects:
	
	- Installation of IIS 5.0
	- Online Help and Documentation
	- Programming and Developing
	- Security Information and Considerations
	- Usage
	- Troubleshooting and Support
	- Miscellaneous Information and References
	
	MORE INFORMATION
	================
	
	Installation of IIS 5.0
	-----------------------
	
	NOTE: IIS 5.0 is an integrated component of Windows 2000. Unlike IIS 4.0, it is
	not available as a separate download.
	
	Upgrade Path:
	
	- Windows NT 4.0 Server: If you upgrade Windows NT Server 4.0 to Windows 2000
	  Server, IIS 5.0 is automatically installed.
	
	- Windows 95, Windows 98, or Windows NT Workstation 4.0: If you upgrade Windows
	  95, Windows 98, or Windows NT Workstation 4.0 to Windows 2000 Professional,
	  by default, IIS 5.0 is not installed unless Personal Web Server (PWS) has
	  already been installed on the computer.
	
	  For more information, see Run IIS 5.0 Instead of PWS on Windows 2000
	  Professional
	  (http://support.microsoft.com/support/kb/articles/q262/6/32.asp).
	
	Pre-Installation Checklist:
	
	- Moving from a non-Microsoft Web server to IIS: For information on migrating
	  from other Web servers, see the TechNet article Getting Ready for IIS 5.0
	  (http://www.microsoft.com/TechNet/iis/ready.asp).
	
	- Windows 2000 System Requirements:
	  http://www.microsoft.com/windows2000/upgrade/
	
	- IIS Topics in the Windows 2000 Help: Initial information about using IIS,
	  including how to install it, a software checklist, and how to test your new
	  IIS installation are all located in the Windows 2000 Help file in the
	  following location:
	
	  Internet Tools and Services\Internet Information Services
	
	- Installing on a stand-alone or member server computer: In addition to the
	  heavy load that is placed on a computer acting as both a Domain Controller
	  and IIS server, synchronization problems such as those described in the
	  Microsoft Knowledge Base article Q190005, A Site Set Up for Anonymous Access
	  Prompts Users for Password
	  (http://support.microsoft.com/support/kb/articles/q190/0/05.asp) can occur.
	
	Manually Installing IIS 5.0:
	
	NOTE: When you install IIS, you can choose among several subcomponents in IIS.
	For information on what each subcomponents does, see
	http://www.microsoft.com/windows2000/server/evaluation/features/web.asp.
	
	If IIS 5.0 has not already been installed on your Windows 2000 computer, perform
	the following steps to install it:
	
	1. On the Start menu, click Control Panel, and then click "Add/Remove Programs".
	
	2. Select "Add/Remove Windows Components", select the Internet Information
	  Services (IIS) component, and then follow the on-screen instructions.
	
	Online Help and Documentation
	-----------------------------
	
	- Local online documentation: When a default installation of IIS is performed,
	  the documentation is installed on the local computer, and viewed by using the
	  URL http://localhost/iisHelp/.
	
	- Internet-Based Documentation: Additionally, this documentation is also
	  available at http://windows.microsoft.com/windows2000/en/server/iis/.
	
	- Book: This documentation is also available in the Microsoft Press book,
	  Microsoft(R) Internet Information Services 5.0 Documentation
	  (http://mspress.microsoft.com/prod/books/3250.htm).
	
	Programming and Developing
	--------------------------
	
	- Microsoft TechNet - Windows Web Services (IIS)
	  (http://www.microsoft.com/technet/iis/)
	
	- Microsoft Developer Network (MSDN): Server Technologies
	  (http://msdn.microsoft.com/workshop/c-frame.htm?/workshop/server/)
	
	- Internet Information Services SDK
	  (http://msdn.microsoft.com/library/psdk/iisref/psdkwelc.htm): The SDK
	  provides detailed information about creating ASP pages and developing Web
	  applications. It also describes the event methods and interfaces available
	  for creating components that can be accessed by ASP or ISAPI extensions. The
	  SDK also contains information on how to store your custom IIS configuration
	  data and how you can use built-in objects to manipulate that data, and how
	  you can log server activity. Also, the SDK provides a library of script and
	  program samples that demonstrate a variety of ways to interact with IIS
	  programmatically.
	
	Debugging:
	
	NOTE: Debug Symbol files (symbols) are required to do both kernel and user-mode
	debugging in Windows NT. Symbols provide a way to resolve global variables and
	function names in the loaded executable file.
	
	Symbols are produced by the linker when a program is built. They are removed from
	the retail product and saved in a separate (.dbg) file. This considerably
	reduces file size, which decreases file load time and therefore increases system
	performance. Symbols represent Function/API names and global variables.
	
	- Windows 2000 symbols: The symbols used by IIS are included in the Windows
	  2000 symbols, which are available at the following locations:
	
	   - The "Customer Support and Diagnostics Tools" CD, which is included with
	     Windows 2000 Server and Advanced Server.
	
	   - http://www.microsoft.com/Windows2000/downloads/otherdownloads/symbols/download.asp
	
	- Platform SDK Windows 2000 Debuggers
	  (http://msdn.microsoft.com/downloads/default.asp?URL=/code/topic.asp?URL=/MSDN-FILES/028/000/015/topic.xml):
	  Windows 2000 Debuggers contain a graphical debugger you can use to debug
	  Microsoft Win32-based applications. On Microsoft Windows NT or Windows 2000,
	  you can also use the debuggers to debug kernel-mode drivers. The Windows 2000
	  Debuggers are included in the Platform Software Development Kit (SDK) and the
	  Windows 2000 Driver Development Kit (DDK).
	
	- Microsoft Windows NT and Windows 2000 Debugging Resources
	  (http://www.microsoft.com/hwdev/driver/ntdebugging.htm)
	  This package is also included in both the Platform SDK and the Windows 2000
	  DDK. Both the SDK and DDK are both available through MSDN. This also includes
	  links to the following resources:
	
	   - The Microsoft Debugging Tools Knowledge Base Articles are a collection of
	     Product Support articles that are relevant to debugging.
	
	   - The Resources for Microsoft Debugging Tools page is a collection of
	     pointers to various resources, from Microsoft and from other third
	     parties, that may be useful to those who are interested in debugging.
	
	   - The OEM Support Tools Phase 3 Service is another debugger package to
	     investigate. It currently contains a few tools which aren't included in
	     the normal debugger package.
	
	Security Information and Considerations
	---------------------------------------
	
	- Microsoft Security Bulletin Search
	  (http://www.microsoft.com/technet/security/current.asp?productID=15)
	
	- Windows 2000 Internet Server Security Configuration Tool for IIS 5
	  (http://www.microsoft.com/Downloads/Release.asp?ReleaseID=19889)
	
	- How to Use the IIS Security "What If" Tool
	  (http://support.microsoft.com/support/kb/articles/q229/6/94.asp)
	
	- Microsoft Security Advisor Program: Microsoft Internet Information Server
	  (http://www.microsoft.com/security/products/iis.asp)
	
	Usage
	-----
	
	- Remote Administration: You can administer an IIS computer remotely using the
	  MMC-based Internet Service Manager, the HTML-Based Internet Service Manager
	  (commonly also known as WebAdmin or HTMLA), or Terminal Services.
	
	- The Art and Science of Web Server Tuning with Internet Information Services
	  5.0 (http://www.microsoft.com/windows2000/library/operations/web/tuning.asp):
	  This white paper describes the issues and approaches involved in tuning a Web
	  server when running Internet Information Services 5.0 on Windows 2000 Server.
	  It discusses the importance of monitoring and testing, as well as potential
	  hardware, software, and tools issues that may arise. There is a section on
	  new or changed IIS and Windows 2000 settings and features, and there are a
	  number of appendixes that list useful tips, registry and metabase settings,
	  and resources for your reference. Although this document is written
	  specifically for IIS 5.0, much of this material may also be useful for IIS
	  4.0 administrators
	
	- Deploying Windows 2000 with IIS 5.0 for Dot Coms: Best Practices
	  (http://www.microsoft.com/windows2000/library/planning/incremental/iisdotcom.asp)
	  This paper recommends a series of best practices for deploying the Windows
	  2000 operating system and Internet Information Services 5.0 in a dot-com
	  environment. The information and conclusions in this document were compiled
	  while deploying systems for major dot-com businesses in the Windows 2000
	  Joint Development Program. Each section provides links to online documents
	  that are helpful in carrying out these recommendations.
	
	- Internet Information Services 5.0 Technical Overview
	  (http://www.microsoft.com/WINDOWS2000/library/howitworks/iis/iis5techoverview.asp)
	  This white paper gives information technology professionals a technical
	  overview of the new features provided by Internet Information Services 5.0,
	  delivered with the Windows 2000 operating system. These features include
	  reliability and performance improvements such as Reliable Restart,
	  Application Protection, and support for clustering. The paper also includes
	  an extensive look at security provisions, and introduces new security
	  protocols supported by IIS 5.0, including Transport Layer Security and Digest
	  Authentication. For those who are using the Internet to share information,
	  Web Distributed Authoring and Versioning (WebDAV) is also introduced.
	  Application developers can find descriptions of a number of improvements to
	  Active Server Pages (ASP).
	
	Troubleshooting and Support
	---------------------------
	
	The following tools and resources are available to help you isolate problems,
	troubleshoot, and get technical support:
	
	- Information from IIS Product Support Services: FAQs & Highlights for Internet
	  Information Services 5.0
	  (http://support.microsoft.com/support/default.asp?PR=iisvce&FR=0&SD=MSDN&LN=EN-US)
	
	- AutoDump Plus: A utility used for troubleshooting advanced IIS issues (for
	  example, Access Violation error messages, services that stop responding, and
	  100 percent CPU usage). For more information, see the Microsoft Knowledge
	  Base Article Q286350, HOWTO: Use Autodump+ to Troubleshoot 'Hangs' and
	  'Crashes' (http://support.microsoft.com/support/kb/articles/Q286/3/50.asp).
	
	- Microsoft Web Application Stress Tool: This is a simulation tool that is
	  designed to realistically reproduce multiple browsers requesting pages from a
	  Web application. It was developed by Web testers and is easy to use.
	  Microsoft recommends that you use this tool to gather performance data on
	  your Web site. For more information, see Q231282, INFO: Stress Tools to Test
	  Your Web Server
	  (http://support.microsoft.com/support/kb/articles/Q231/2/82.asp).
	
	- MetaEdit 2.1:
	  (http://support.microsoft.com/support/kb/articles/Q232/0/68.ASP) Utility for
	  troubleshooting and modifying metabase values.
	
	- Internet Information Server Newsgroups
	  (http://support.microsoft.com/isapi/gosupport.asp?target=/newsgroups/)
	
	Miscellaneous Information and References
	----------------------------------------
	
	- Internet Information Server (version 4.0) is now named Internet Information
	  Services (version 5.0) in Windows 2000.
	
	- Recommended Configurations and Installation Procedures for Site Server 3.0
	  (http://support.microsoft.com/support/siteserver/install/install_ss3.asp).
	
	- MDAC version 2.5 is included in Windows 2000. For the latest information
	  about MDAC, see http://www.microsoft.com/data.
	
	- Internet Explorer version 5.0 is included in Windows 2000. For the latest
	  information about Internet Explorer, see
	  http://www.microsoft.com/windows/ie/.
	
	- Exploring Web & Application Services Product Guide
	  (http://www.microsoft.com/windows2000/technologies/web/default.asp)
	
	Additional query words: iis 5 tips tricks gotchas hints setup set up utilizing
	
	======================================================================
	Keywords          : kbOSWin2000 
	Technology        : kbiisSearch kbiis500
	Version           : :5.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
