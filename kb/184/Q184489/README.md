---
layout: page
title: "Q184489: SMS: Despooler May Delete Package Dir Contents If Files in Use"
permalink: /kb/184/Q184489/
---

## Q184489: SMS: Despooler May Delete Package Dir Contents If Files in Use

	Article: Q184489
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:1.2
	Operating System(s): 
	Keyword(s): kbDespooler smsdespoolerkbbuglist
	Last Modified: 31-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 1.2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When Despooler is unable to refresh package files that are currently in use by
	clients, the entire contents of the package directory may be deleted. However, a
	retry instruction should be created for Despooler, and the package directory
	will eventually be repopulated.
	
	CAUSE
	=====
	
	The process Despooler uses to update package files involves deleting the files
	first and then copying over the refreshed package files from a temporary
	directory. Despooler does not check to see if it can refresh the package files
	before performing the deletion request. Despooler succeeds in the deletion
	request but is unable to refresh files that are in use. As a result, the entire
	contents of the package directory are deleted.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	version 1.2. This problem has been corrected in the latest U.S. service pack for
	Systems Management Server version 1.2. For information on obtaining the service
	pack, query on the following word in the Microsoft Knowledge Base (without the
	spaces):
	
	  S E R V P A C K
	
	WORKAROUND
	==========
	
	To work around this problem, contact Microsoft Technical Support to obtain the
	following fix, or wait for the next Systems Management Server service pack. The
	hotfix should have the following timestamp:
	
	  4/2/98   1:37pm      252,848 Smsinst.dll (Intel)
	  4/2/98   1:37pm      480,016 Smsinst.dll (Alpha)
	
	You can also use the Use Forced Disconnect functionality of Despooler as a
	workaround. However, this functionality does not support Macintosh clients.
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbDespooler smsdespooler kbbuglist
	Technology        : kbSMSSearch kbSMS120
	Version           : winnt:1.2
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	