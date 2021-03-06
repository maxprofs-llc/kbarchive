---
layout: page
title: "Q303848: SMS: Data Access/Share Name Box Is Limited to 64 Characters"
permalink: /kb/303/Q303848/
---

## Q303848: SMS: Data Access/Share Name Box Is Limited to 64 Characters

{% raw %}

	Article: Q303848
	Product(s): Microsoft Systems Management Server
	Version(s): 2.0,2.0 SP1,2.0 SP2,2.0 SP3,2.0 SP4
	Operating System(s): 
	Keyword(s): kbsms200 kbsms200bug kbsms120 kbsms120bug
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 2.0, 2.0 SP1, 2.0 SP2, 2.0 SP3, 2.0 SP4 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you create a new package in the Systems Management Server (SMS)
	Administrator console, you cannot type more than 64 characters in the "Share
	name" box on the Data Access tab.
	
	Note that you type a share name in the "Share name" box when you want to create a
	package share on distribution points rather than using the default SMSPKGx$
	share.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem that is described in this article. Only apply it to systems
	that are experiencing this specific problem. This fix may receive additional
	testing. Therefore, if you are not severely affected by this problem, Microsoft
	recommends that you wait for the next SMS service pack that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, visit the following Microsoft
	Web site:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are ordinarily incurred for support calls
	may be canceled if a Microsoft Support Professional determines that a specific
	update will resolve your problem. The usual support costs will apply to
	additional support questions and issues that do not qualify for the specific
	update in question.
	
	The English-language version of this fix for SMS Service Pack 3 (SP3) sites
	should have the following file attributes or later:
	
	  Date         Time   Version         Size     File name     Platform
	  -------------------------------------------------------------------
	  01-Mar-2001  11:25  2.00.1493.3181  127,168  Sms_ppkg.dll  Intel
	  05-Sep-2001   9:37                    3,395  Update.sql    Intel
	  01-Mar-2001  11:25  2.00.1493.3181  264,464  Sms_ppkg.dll  Alpha
	  05-Sep-2001   9:37                    3,395  Update.sql    Alpha
	
	Post-SP4 hotfix information:
	
	 
	  Date         Time   Size     File name     Platform  Version
	  ------------------------------------------------------------------
	  01-Mar-2002  08:00  127,168  Sms_ppkg.dll  Intel     2.0.1493.4101
	  26-Nov-2001  15:50    3,395  Update.sql    Intel
	  01-Mar-2002  08:00  264,464  Sms_ppkg.dll  Alpha     2.0.1493.4101
	
	NOTE: Due to file dependencies, the most recent hotfix or feature that contains
	the above files may also contain additional files.
	
	
	
	After you install this hotfix, you can type up to 127 characters in the "Share
	name" box.
	
	
	How to Install the Hotfix
	-------------------------
	
	To install the hotfix, use one of the following methods. Note that you should
	install the hotfix on primary site servers and computers that are running the
	SMS Administrator console. You do not need to install the fix on secondary site
	servers.
	
	How to Use the Hotfix Installer on Site Servers and Computers That Are Running the SMS Administrator Console:
	
	NOTE: You can use this method only on Intel-based computers.
	
	To use the hotfix installer on site servers and computers that are running the
	SMS Administrator console:
	
	1. Create a folder in a location that is accessible to your SMS site server or
	  site servers.
	
	2. Log on to your site server by using an account with administrative
	  privileges.
	
	3. Copy the Q303848.exe update file and platform folders to the new folder. The
	  Q303848.exe file must be one folder higher than the platform folders.
	
	4. From each of the primary SMS site servers and from the computers with the SMS
	  Administrator console installed, run Q303848.exe. Follow the prompts to
	  install the hotfix.
	
	How to Manually Install the Hotfix on Site Servers:
	
	To manually install the hotfix on site servers:
	
	1. Copy the hotfix folder structure to a local subfolder on your site server or
	  to a share on your network.
	
	2. Close the SMS Administrator console and stop all SMS services.
	
	3. Replace the Sms_ppkg.dll file in the
	  <Sms_root_folder>\Bin\<Platform> folder with the version of the
	  file that you obtained from the hotfix.
	
	4. Run the SQL Query Analyzer tool (Isqlw.exe). Note that you must:
	
	  a. Click Change Database on the Query menu.
	
	  b. Click the SMS database.
	
	  c. Click Open on the File menu.
	
	  d. Locate and click the Update.sql script that is included with this hotfix,
	     and then press ENTER.
	
	  e. Click Execute on the Query menu to run the script.
	
	5. Restart all SMS services.
	
	How to Manually Install the Hotfix on Computers That Have the SMS Administrator Console Installed:
	
	To manually install the hotfix on computers that have the SMS Administrator
	console installed:
	
	1. Copy the hotfix folder structure to a local subfolder on your computer or to
	  a share on your network.
	
	2. Close the SMS Administrator console.
	
	3. Replace the Sms_ppkg.dll file in the Smsadmin\Bin\<Platform> folder
	  with the version of the file that you obtained from the hotfix.
	
	
	WORKAROUND
	==========
	
	To work around this problem, organize distribution points so that paths to
	package shares are less than 64 characters in length. Note that the server name
	is not part of the path that you type in the "Share name" box.
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in the Microsoft products that
	are listed at the beginning of this article. This problem was first corrected in
	the Systems Management Server 2.0 Service Pack 4 Hotfix Rollup Package (HRP).
	
	For additional information about the SMS 2.0 SP4 HRP, click the article number
	below to view the article in the Microsoft Knowledge Base:
	
	  Q323206 SMS: List of Bugs Fixed in the Systems Management Server 2.0 SP4 HRP
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbsms200 kbsms200bug kbsms120 kbsms120bug 
	Technology        : kbSMSSearch kbSMS200 kbSMS200SP1 kbSMS200SP2 kbSMS200SP3 kbSMS200SP4
	Version           : :2.0,2.0 SP1,2.0 SP2,2.0 SP3,2.0 SP4
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
