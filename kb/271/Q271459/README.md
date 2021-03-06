---
layout: page
title: "Q271459: IIS 4.0: Can't Extract Data from Access on Netware 5 Server"
permalink: /kb/271/Q271459/
---

## Q271459: IIS 4.0: Can't Extract Data from Access on Netware 5 Server

{% raw %}

	Article: Q271459
	Product(s): Internet Information Server
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 19-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Server 4.0 
	- Microsoft OLE DB Provider for Jet, version 4.0 
	- Microsoft ODBC Driver for Access, version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A Microsoft Access database exists on a Netware 5 Server volume that is running
	only the TCP/IP protocol. By using either Open Database Connectivity (ODBC) or
	OLE Provider for Jet, an error message is returned that states that the file
	cannot be found. There are no errors in the event logs and the ODBC connection
	tests successfully. If you are using ODBC Driver for access, the error message
	is:
	
	  Microsoft OLE DB Provider for ODBC Drivers error '80004005'
	
	  [Microsoft][ODBC Microsoft Access Driver] '(unknown)' is not a valid path.
	  Make sure that the path name is spelled correctly and that you are connected
	  to the server on which the file resides.
	
	If you are using the OLE DB Provider for Jet, the error message is:
	
	  Microsoft JET Database Engine error '80004005'
	
	  'UNC Path Name will be here' is not a valid path. Make sure that the path name
	  is spelled correctly and that you are connected to the server on which the
	  file resides.
	
	CAUSE
	=====
	
	For access to be granted to the Netware File System, credentials must be passed
	that have the appropriate rights to the databases that you are attempting to
	access. By default, IIS attempts to pass credentials for the IUSER_MachineName
	account.
	
	Netware uses the Netware Directory Service to authenticate users to its servers.
	In order to access any file systems, a legitimate account for the credentials
	being passed must exist on the Netware server.
	
	RESOLUTION
	==========
	
	To properly communicate with Microsoft Access Databases on a Netware 5 server by
	running only TCP/IP, please follow these steps exactly:
	
	1. On the IIS server that you want to communicate with Access, install Novell
	  Netware Client for Windows NT (Required). During setup, choose a Custom
	  Installation, choose to install into a NDS system, and choose only ip for the
	  protocol.
	
	  IMPORTANT NOTE: Do not install Workstation Manager.
	
	
	2. Install MDAC 2.5, which you can find at the following Microsoft Web site:
	
	  http://www.microsoft.com/data/ (http://www.microsoft.com/data/)
	
	3. Create an ODBC System DSN using the Microsoft Access Database driver:
	
	   - Click Select, and then enter the path to the database by using Universal
	     Naming Convention (UNC) in the database name field to give the DSN a name.
	
	-or-
	
	   - Add an OLE DB Provider for Jet Connection String to the asp page that is
	     failing. An example of a Access Connection String is:
	
	  set conn = server.CreateObject("ADODB.Connection")
	  conn.open "Provider=Microsoft.Jet.OLEDB.4.0;Data Source='UNC Path to Netware 5 Goes Here';Persist Security Info=False"
	
	4. On the Windows NT IIS server, use User Manager to change the IUSR password:
	
	  a. In the Internet Service Manager, open the properties of the localhost. In
	     the Master Properties section, click Edit.
	
	  b. Click the Directory Security tab. In the Anonymous access section, click
	     Edit, and then deselect NT to synchronize the password.
	
	  c. Change the password to match the one that was set in User Manager.
	
	  d. Stop and restart the IIS Services and test that Anonymous access is still
	     working.
	
	5. Open the Netware Administrator found on the sys: volume under Public\WIN32
	  folder of the Netware 5 server. In the root of the container at which the
	  server exists, create a IUSR_Machine Name account identical to the one that
	  is on the Windows NT Server. On the properties of that user, click Password
	  Restrictions and choose to have Require password checked. Click the Set
	  Password button, and set the password to that of the NT account.
	
	  IMPORTANT NOTE: Do not require passwords to be changed on the Netware system.
	  This is the most crucial step to the entire process.
	
	6. In Netware Administrator, under the newly created IUSR properties, choose the
	  Rights to files and directories tab, and then add the appropriate rights to
	  the database files that need to accessed. At the least, READ permissions need
	  to be given, unless changes are made through the Internet that require all
	  permissions except supervisor and access control.
	
	  NOTE: This process of configuring proper authentication could also be
	  accomplished by granting rights to a NDS group object (that is, Web Access
	  Group), and then making the IUSR_MachineName a member of this group.
	
	
	WORKAROUND
	==========
	
	If the preceding resolution is not satisfactory, a workaround can be produced
	that is typically used in older Netware versions. By using GSNW, a connection to
	the Netware 5 server could be established using the IPX/SPX protocol. However,
	please note that this requires that IPX be added to the Netware 5 Server as well
	as the Windows NT Server.
	
	
	For installation instructions for the GSNW, please refer to the Windows NT 4.0
	End-User Manual.
	
	MORE INFORMATION
	================
	
	For additional information regarding these procedures using IIS 5.0, click the
	article number below to view the article in the Microsoft Knowledge Base:
	
	  Q271228 Unable to Obtain Data from Access Database Residing on Netware 5
	  Server Using ASP
	
	The third-party products discussed in this article are manufactured by vendors
	independent of Microsoft; we make no warranty, implied or otherwise, regarding
	these products' performance or reliability.
	
	Additional query words: foxpro iis 80004005
	
	======================================================================
	Keywords          :  
	Technology        : kbiisSearch kbAudDeveloper kbAccessSearch kbiis400 kbODBCSearch kbOLEDBSearch kbODBCAccess400 kbOLEDBProvJet400 kbOLEDBProvSearch
	Version           : :4.0
	Issue type        : kbprb
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
