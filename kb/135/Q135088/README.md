---
layout: page
title: "Q135088: Typing Full Path and Filename Causes Inventory Rule to Fail"
permalink: /kb/135/Q135088/
---

## Q135088: Typing Full Path and Filename Causes Inventory Rule to Fail

{% raw %}

	Article: Q135088
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:1.0,1.1,1.2
	Operating System(s): 
	Keyword(s): kbnetwork kbConfig kbInventory smsinv smsconfig
	Last Modified: 25-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 1.0, 1.1, 1.2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	
	If you add an inventory rule for a package in the Systems Management Server
	Administrator File Properties dialog box and type the full path to the file and
	the filename, the following symptoms occur:
	
	- The inventory agent is unable to find the file.
	
	- If you add a property such as Checksum to the rule, you cannot obtain the
	  value for that property.
	
	CAUSE
	=====
	
	The rule parser requires that you type only the filename without the full path
	to the file.
	
	WORKAROUND
	==========
	
	To work around this problem, type the filename without the path to the file.
	
	To retrieve the value of a property for the rule, choose the Browse button to
	find the file (instead of typing the filename).
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	versions 1.0, 1.1 and 1.2. We are researching this problem and will post new
	information in the Microsoft Knowledge Base as it becomes available.
	
	Additional query words: prodsms sms software invdos package.rul
	
	======================================================================
	Keywords          : kbnetwork kbConfig kbInventory smsinv smsconfig 
	Technology        : kbSMSSearch kbSMS100 kbSMS110 kbSMS120
	Version           : winnt:1.0,1.1,1.2
	
	=============================================================================
	

{% endraw %}
