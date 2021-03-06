---
layout: page
title: "Q226888: SMS: Component Status Times Listed Ahead Of Local Time in GMT"
permalink: /kb/226/Q226888/
---

## Q226888: SMS: Component Status Times Listed Ahead Of Local Time in GMT

{% raw %}

	Article: Q226888
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:2.0
	Operating System(s): 
	Keyword(s): kbsms200 kbsms200bug kbsms120 kbsms120bug
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 2.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When viewing the status summary of components in Systems Management Server 2.0,
	the Last Started and Last Message columns for each component may display future
	dates.
	
	Navigate to Site Database\System Status\Site Status\SiteName\Component Status to
	see the status summary of your components.
	
	This future date can cause a problem when the Status Message Viewer is launched
	against a component. The Status Message Viewer will return an empty result set
	for every display interval except Since Site Installation.
	
	The display interval for the Status Message Viewer can be set by right- clicking
	Component Status and selecting a display interval.
	
	WORKAROUND
	==========
	
	To resolve this problem, obtain the latest service pack for Systems Management
	Server 2.0. For additional information, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q236325 SMS: How to Obtain the Latest Systems Management Server 2.0 Service
	  Pack
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Systems Management Server 2.0.
	This problem was first corrected in Systems Management Server 2.0 Service Pack
	Service Pack 1.
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbsms200 kbsms200bug kbsms120 kbsms120bug 
	Technology        : kbSMSSearch kbSMS200
	Version           : winnt:2.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
