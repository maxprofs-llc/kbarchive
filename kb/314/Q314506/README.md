---
layout: page
title: "Q314506: HOW TO: Use Internet Explorer to Verify Your IIS Security Config"
permalink: /kb/314/Q314506/
---

## Q314506: HOW TO: Use Internet Explorer to Verify Your IIS Security Config

{% raw %}

	Article: Q314506
	Product(s): Internet Information Server
	Version(s): 5.0
	Operating System(s): 
	Keyword(s): kbAudITPro kbHOWTOmaster
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Services version 5.0 
	-------------------------------------------------------------------------------
	
	IN THIS TASK
	------------
	
	- SUMMARY
	
	   - Check the Server Agent, ISAPI DLL
	- Verify IIS Security Settings
	
	- REFERENCES
	
	SUMMARY
	=======
	
	You can use Microsoft Internet Explorer to determine the security settings of
	your Internet Information Services (IIS) 5.0 configuration. You can also check
	the server agent, ISAPI DLL, to verify that you have configured the agent
	correctly. This article summarizes the necessary steps to ensure that your
	servers are properly secured.
	
	NOTE: In addition to IIS, you need some familiarity with Microsoft SQL Server
	2000 CE to perform the procedures in this article.
	
	Check the Server Agent, ISAPI DLL
	---------------------------------
	
	You can use Internet Explorer to verify that your server agent, ISAPI DLL, is
	configured properly. To do this, type the following in the Address bar in
	Internet Explorer, and then press ENTER:
	
	  http://<my server>/sqlce/sscesa10.dll
	
	NOTE: If you configured IIS to use Secure Sockets Layer (SSL), change http:// to
	"https://" (without the quotation marks).
	
	If you configured your server agent properly, the string "Body" will be
	displayed.
	
	Verify IIS Security Settings
	----------------------------
	
	You can verify that your IIS security settings are correct while you check ISAPI
	DLL. To do this, follow these steps:
	
	1. Type the following in the Address bar of Internet Explorer, and then press
	  ENTER:
	
	  http://<my server>/
	
	  NOTE: If you configured IIS to use SSL, change the http:// to "https://"
	  (without the quotation marks).
	
	2. If you configured IIS for Basic authentication, you will be prompted for your
	  user name and password.
	
	  If you are not prompted for a name and password, you have configured your IIS
	  for anonymous access without any authentication.
	
	  NOTE: Be sure to click Refresh on the Internet Explorer toolbar after you make
	  changes to your server. This ensures that Internet Explorer does not read
	  from the cache.
	
	REFERENCES
	----------
	
	For more information, browse to the following MSDN Web site:
	
	  SQL Server 2000 CE Books Online
	  http://msdn.microsoft.com/library/default.asp?url=/library/en-us/sqlce/portal_6ol0.asp?frame=true
	
	Additional query words:
	
	======================================================================
	Keywords          : kbAudITPro kbHOWTOmaster 
	Technology        : kbiisSearch kbiis500
	Version           : :5.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
