---
layout: page
title: "Q263401: SMS: Software Inventory Recalls all Remote Offline Storage"
permalink: /kb/263/Q263401/
---

## Q263401: SMS: Software Inventory Recalls all Remote Offline Storage

{% raw %}

	Article: Q263401
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:2.0,2.0 SP1,2.0 SP2
	Operating System(s): 
	Keyword(s): kbtool kbsms200 kbsms200bug kbsms200preSP3
	Last Modified: 27-OCT-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 2.0, 2.0 SP1, 2.0 SP2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When the Systems Management Server (SMS) client software inventory agent runs on
	a Windows 2000-based computer with significant amounts of remote storage (such
	as a tape autoloader), it cycles through all of the offline storage tapes, and
	restores all of the files back onto the computer's hard disk for inventory.
	
	This causes the remote storage system to continuously move files to and from
	remote storage, trying to adhere to storage limits on each volume while
	providing files to inventory.
	
	Because of this, inventory may never finish and the tape system and disk
	sub-systems may be very busy.
	
	CAUSE
	=====
	
	This problem can occur because when software inventory opens files to read
	header information, Windows 2000 recalls the remote copy from remote storage
	(such as tape media) to the local hard disk before opening the file.
	
	WORKAROUND
	==========
	
	To work around this problem, on the client that has remote storage configured,
	disable software inventory on each drive by creating a hidden file named
	Skpswi.dat and place it in the root folder of the drive. Software inventory does
	not run again on these drives until the Skipswi.dat file is removed.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	version 2.0.
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbtool kbsms200 kbsms200bug kbsms200preSP3 
	Technology        : kbSMSSearch kbSMS200 kbSMS200SP1 kbSMS200SP2
	Version           : winnt:2.0,2.0 SP1,2.0 SP2
	Issue type        : kbbug
	Solution Type     : kbnofix
	
	=============================================================================
	

{% endraw %}
