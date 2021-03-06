---
layout: page
title: "Q325864: HOW TO: Install and Use the IIS Lockdown Wizard"
permalink: /kb/325/Q325864/
---

## Q325864: HOW TO: Install and Use the IIS Lockdown Wizard

{% raw %}

	Article: Q325864
	Product(s): Internet Information Server
	Version(s): 4.0,5.0
	Operating System(s): 
	Keyword(s): kbHOWTOmaster
	Last Modified: 02-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Services version 5.0 
	- Microsoft Internet Information Services version 5.1 
	- Microsoft Internet Information Server version 4.0 
	-------------------------------------------------------------------------------
	
	
	IN THIS TASK
	------------
	
	- SUMMARY
	
	   - Prepare to Run the IIS Lockdown Wizard
	   - Download and Install the IIS Lockdown Wizard
	   - Configure URLScan
	   - Troubleshoot Problems After You Run the IIS Lockdown Wizard
	
	- REFERENCES
	
	SUMMARY
	=======
	
	This step-by-step article explains how to secure a Web server by using the
	Internet Information Services (IIS) Lockdown Wizard. It also includes
	information about how to troubleshoot problems that occur after you run the
	wizard.
	
	Prepare to Run the IIS Lockdown Wizard
	--------------------------------------
	
	With the IIS Lockdown Wizard, you can disable several optional features of IIS to
	secure your IIS server against attack. Before you run the wizard, read the Help
	file to familiarize yourself with the options that the wizard presents. To
	access the help file:
	
	1. Download the IIS Lockdown Wizard. To download the wizard, visit the following
	  Microsoft Web site:
	
	  http://www.microsoft. com/Downloads/Release.asp?ReleaseID=33961
	
	2. Extract the Lockdown Wizard files from the executable file.
	
	For additional information, click the article number below to view the article in
	the Microsoft Knowledge Base:
	
	  Q315522 HOW TO: Extract the URLScan Tool and Lockdown Template Files from the
	  IIS Lockdown Tool
	
	3. Find the folder that you specified when you extracted the files, and then
	  double-click the Iislockd.chm file.
	
	Note that the Lockdown Wizard permits you to disable certain optional features of
	IIS that are required for the correct operation of other applications, such as
	Exchange and FrontPage. If you do not select the correct options when you run
	the Lockdown Wizard, you may break the functionality of these applications. To
	minimize problems, carefully review the Microsoft Knowledge Base articles that
	are appropriate to your system configuration before you run the Lockdown
	Wizard:
	
	- Exchange and Outlook Web Access (OWA):
	
	  Q309508 XCCC: IIS Lockdown and URLscan Configurations in an Exchange
	  Environment
	
	- Microsoft Mobile Information Server:
	
	  Q311595 XCCC: How to Install and Configure Microsoft Security Tool Kit On a
	  Microsoft Mobile Information Server
	
	- Microsoft Small Business Server:
	
	  Q311862 How to Use The IIS Lockdown Tool with Small Business Server
	
	- Microsoft Project, Project Server, and Project Web Access:
	
	  Q321357 PSRV2002: Error Messages When You View a Microsoft Project Web Access
	  Page That Contains Grids
	
	  Q316398 PRJ2000: Configuring the IIS Lockdown Tool and URLScan Security Tool
	  with Microsoft Project Central
	
	- Microsoft SharePoint Portal Server:
	
	  Q309675 SPS: IIS Lockdown Tool Affects SharePoint Portal Server
	
	  Q319633 SPS: 'Script Execution Error: Error Executing INVOKE' Error Message
	  After You Install IIS Lockdown Wizard
	
	- Microsoft Visual Studio .NET:
	
	  Q310588 PRB: Security Toolkit Breaks ASP.NET Debugging in Visual Studio .NET
	
	  Q315904 BUG: 'ExternalException: Cannot Execute a Program' Error Message When
	  You Call WebServices from .aspx Page
	
	- Microsoft FrontPage:
	
	  Q317390 FP2002: 'HTTP/1.1 404 Object Not Found' Error Message Occurs When a
	  User of Your Web Page Performs a Search
	
	  Q307976 FP: Error Message When You Use FrontPage with URLScan
	
	- Microsoft Proxy Server:
	
	  Q311675 Cannot Search Proxy Server 2.0 Online Help After the IIS Lockdown
	  Wizard Is Installed
	
	Download and Install the IIS Lockdown Wizard
	--------------------------------------------
	
	1. Double-click the executable file that you downloaded in the Prepare to Run
	  the IIS Lockdown Wizard section to start the wizard.
	
	2. On the Welcome page, read the explanatory text, and then click Next.
	
	3. On the License Agreement page, read the license agreement, click I Agree, and
	  then click Next.
	
	4. On the Select Server Template page, select the template that most closely
	  matches the role of this server, and then click to select View Template
	  Settings. The pages that follow this have options already selected based on
	  the role of the server that you selected earlier in the previous page, so you
	  can use all of the default selections.
	
	  If the server has multiple roles (for example, a dynamic Web server that is
	  also a proxy server), click to select Other (Server that does not match any
	  of the listed roles), and make sure that you carefully consider all the
	  options that are presented on the following pages, because the default
	  selections may not be appropriate for your server. When you have selected the
	  appropriate settings, click Next.
	
	5. On the Internet Services page, select the services that you want your server
	  to provide. Most servers require the Web service. If you do not want your
	  server to provide File Transfer Protocol (FTP) or Simple Mail Transfer
	  Protocol (SMTP) services (that is, file transfer or e-mail services), you can
	  click to clear these options. Note that you must leave SMTP selected if you
	  are running Exchange or Small Business Server.
	
	  The services that you select on this page are set to Disabled and cannot
	  start. If you are running the Lockdown Wizard on IIS 5.0, you can also click
	  to select Remove unselected services, which completely removes the services
	  that you did not select from your system. When you have selected the
	  appropriate settings, click Next.
	
	6. On the Script Maps page, click to clear the check box next to any file type
	  or file types that you want your server to provide. If you are not sure what
	  to disable, you can search your content directories to find out if those file
	  name extensions exist. Note that most servers require Active Server Pages
	  (.asp), so you must click to clear that check box unless you are sure that
	  your server does not serve ASP pages. Click Next.
	
	7. On the Additional Security page, select the virtual directories that you want
	  to remove from this server. By default, these virtual directories are
	  installed by default with IIS, so they are well-known targets for attackers
	  and you might want to remove these virtual directories or rename them on
	  production computers. Removing these virtual directories from IIS does not
	  remove the corresponding physical directories on the disk, so you do not lose
	  any data by selecting this option.
	
	8. Click to select Running system utilities if you want to deny rights on
	  executable files in the Windows directory to the Internet guest account
	  (IUSR_computername by default). This option should be selected on most
	  systems.
	
	9. Click to select Writing to content directories if you want to deny Write
	  rights to the Internet guest account on the directories that contain your Web
	  content. Make sure that you leave this option unselected if you are using
	  FrontPage Server Extensions on this server or if this server functions as a
	  proxy server.
	
	10. Click to select Disable Web Distributed Authoring and Versioning (WebDAV) if
	  you are not using WebDAV to create and deploy Web content on this server. If
	  this server runs Outlook Web Access (OWA) for Exchange 2000, make sure that
	  you leave this option unselected.
	  NOTE: If you select this option, the Lockdown Wizard sets the rights on the
	  DLL that implements WebDAV functionality (Httpext.dll) to deny execute
	  permission. This may still permit certain WebDAV requests to execute.
	
	For additional information, click the article number below to view the article in
	the Microsoft Knowledge Base:
	
	  Q307934 Locking Down WebDAV Through ACL Still Allows PUT and DELETE Requests
	
	11. Click Next.
	
	12. On the URLScan page, select the option to install URLScan if you want to use
	  URLScan to filter out incoming requests based on a set of rules. If a client
	  tries to make a request that is not valid based on the URLScan rules, IIS
	  replies with a 404 File Not Found error, and logs the request in the URLScan
	  log file. By default, this file is located in
	  %WINDIR%\System32\Inetsrv\Urlscan\Urlscan.log.
	
	  NOTE: If you leave WebDAV enabled on the Additional Security page but you
	  decide to install URLScan, note that URLScan blocks WebDAV requests by
	  default. You must modify the Urlscan.ini file if you want to use WebDAV with
	  URLScan.
	
	13. On the Ready to Apply Settings page, review the changes that will be made,
	  and then click Next.
	
	14. The Lockdown Wizard backs up your metabase and makes the selected changes.
	  When this process has completed, click View Report to see a report that
	  describes the changes that the wizard has made. Click Next to continue.
	
	  NOTE: You can see the installation report by opening
	  %WINDIR%\System32\Inetsrv\Oblt-rep.log in Notepad.
	
	15. Click Finish to close the IIS Lockdown Wizard.
	
	16. Fully test all functionality of your server. This step is very important. If
	  you discover that you have accidentally disabled required functionality of
	  your server, immediately roll back the changes that the Lockdown Wizard
	  made, and then rerun the wizard to select the correct options.
	
	For additional information, click the article number below to view the article in
	the Microsoft Knowledge Base:
	
	  Q317052 HOW TO: Undo Changes Made by the IIS Lockdown Wizard
	
	Configure URLScan
	-----------------
	
	When you run the IIS Lockdown Wizard, you can install URLScan. URLScan is an
	ISAPI filter that blocks HTTP requests based on a configurable set of rules. For
	example, you can configure URLScan to block all requests for a certain file name
	extension, to block certain HTTP verbs (such as GET or POST), or to block
	requests that contain characters that are frequently included in attacks on Web
	servers.
	
	To configure URLScan, use a text editor such as Notepad to edit the
	%WINDIR%\System32\Inetsrv\Urlscan\Urlscan.ini file. This file contains extensive
	comments that explain each configuration option. When you have finished editing
	the .ini file, save it and restart IIS.
	
	For additional information about how to configure URLScan, click the article
	number below to view the article in the Microsoft Knowledge Base:
	
	  Q312376 HOW TO: Configure URLScan to Allow Requests with a Null Extension in
	  IIS
	
	
	Troubleshoot Problems After You Run the IIS Lockdown Wizard
	-----------------------------------------------------------
	
	The most common problem after you run the IIS Lockdown Wizard is receiving
	unexpected 404 File Not Found error messages when you open the locked-down site.
	You may receive these error messages even for files that exist. This occurs when
	a client requests a file that has been blocked by the Lockdown Wizard or
	URLScan. In this case, IIS says that the file does not exist for security
	purposes. If a malicious user knows that a vulnerable service exists on the
	server but is being blocked, the user may still find a way to get around the
	block and exploit the vulnerability; however, if the user thinks that the
	service is not installed, the user will not try to exploit it.
	
	If you receive a 404 error message after you run the IIS Lockdown Wizard, follow
	these steps to troubleshoot the problem:
	
	1. Verify that the file you are requesting exists on the server.
	
	For additional information, click the article number below to view the article in
	the Microsoft Knowledge Base:
	
	  Q248033 Typical Causes and Resolution of the 'HTTP 404 - File Not Found'
	  Error Message
	
	2. Examine the URLScan log file to see if URLScan is blocking the requests. This
	  file is located at %WINDIR%\System32\Inetsrv\Urlscan\UrlscanMMDDYY.log (where
	  MMDDYY is the date for the log). If you discover that URLScan is blocking the
	  requests, see the Configure URLScan section to set up URLScan so it permits
	  these requests.
	
	3. If you are requesting a non-HTML file, such as an ASP page or a server side
	  include-enabled file, verify the application mapping for the file type in the
	  Internet Services Manager:
	
	  a. Right-click your Web site, and then click Properties.
	
	  b. On the Home Directory tab, click Configuration.
	
	  c. Click the Apps Mappings tab.
	
	  d. Click the line that corresponds to the extension of the file that you are
	     trying to access.
	
	  e. If Executable Path is set to %WINDIR%\System32\Inetsrv\404.dll, click
	     Edit, and then set Executable Path to the default executable path for that
	     file extension. If you are not sure of the default, open the
	     %WINDIR%\System32\Inetsrv\oblt-log.log file, which was created when you
	     ran the Lockdown Wizard. Look for a line that starts with SMAP followed by
	     the file name extension. This line also contains the default executable
	     path for that file type.
	
	If you have trouble with a service that depends on IIS, such as Exchange or
	SharePoint, see the Microsoft Knowledge Base articles that are listed in the
	Prepare to Run the IIS Lockdown Wizard section.
	
	You may also find that FTP or SMTP do not work after you run the IIS Lockdown
	Wizard. This occurs if you either disable or remove these services. If you
	disabled the services, follow these steps to re-enable them:
	
	1. Open Control Panel.
	
	2. On Windows NT 4.0, open the Services applet. On Windows 2000 or Windows XP,
	  open the Administrative Tools folder, and then open the Services applet.
	
	3. Double-click FTP Publishing or Simple Mail Transfer Protocol (SMTP).
	
	4. For Startup type, click to select Automatic.
	
	5. Click Start if you want the service to start right away.
	
	If you completely removed one or both of these services by selecting Remove
	unneeded services when you ran the IIS Lockdown Wizard on IIS 5.0, follow these
	steps to reinstall them:
	
	1. Open Control Panel.
	
	2. Open the Add/Remove Programs applet, and then click Add/Remove Windows
	  Components in the left pane.
	
	3. Select Internet Information Services (IIS), and then click Details.
	
	4. Click to select File Transfer Protocol (FTP) Service or SMTP Service.
	
	5. Click OK, and then click Next. The selected service or services will be
	  installed. You may be prompted to insert your Windows CD-ROM.
	
	6. Make sure that you reapply the latest Windows service pack and any hotfixes
	  that you have installed.
	
	If none of these methods works, you can view the IIS Lockdown Wizard report file
	to see all changes that the tool made. This can help you determine what changes
	caused the problems that you are experiencing. This report file is saved at
	%WINDIR\System32\Inetsrv\Oblt-rep.log.
	
	For additional information about how to undo the changes that the IIS Lockdown
	Wizard made, click the article number below to view the article in the Microsoft
	Knowledge Base:
	
	  Q317052 HOW TO: Undo Changes Made by the IIS Lockdown Wizard
	
	REFERENCES
	==========
	
	
	For additional information about the IIS Lockdown Wizard and how to secure your
	IIS server, click the article numbers below to view the articles in the
	Microsoft Knowledge Base:
	
	  Q310725 HOW TO: Run the IIS Lockdown Wizard Unattended in IIS
	
	  Q311350 HOW TO: Create a Custom Server Type for Use with the IIS Lockdown
	  Wizard
	
	  Q282060 Resources for Securing Internet Information Services
	
	Additional query words: iis lockdown tool wizard urlscan harden 404 security toolkit
	
	======================================================================
	Keywords          : kbHOWTOmaster 
	Technology        : kbiisSearch kbiis500 kbiis400 kbiis510
	Version           : :4.0,5.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
