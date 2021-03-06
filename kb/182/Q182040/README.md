---
layout: page
title: "Q182040: XFOR: Internet Mail Service Converts Two-Digit Years Incorrectly"
permalink: /kb/182/Q182040/
---

## Q182040: XFOR: Internet Mail Service Converts Two-Digit Years Incorrectly

{% raw %}

	Article: Q182040
	Product(s): Microsoft Exchange
	Version(s): winnt:5.0,5.5
	Operating System(s): 
	Keyword(s): kbYear2000 kbExchange500preSP3fix
	Last Modified: 22-FEB-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 5.0, 5.5 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you receive a message that has a two-digit year field through the Internet
	Mail Service, the year may not be properly converted to four digits. This
	problem is not likely to occur before the year 2000.
	
	CAUSE
	=====
	
	The Internet Mail Service does not properly convert two-digit years to four
	digits for the year 2000.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 5.0.
	
	
	A supported fix is now available, but has not been fully regression-tested and
	should be applied only to systems experiencing this specific problem. Unless you
	are severely impacted by this specific problem, Microsoft recommends that you
	wait for the next Service Pack that contains this fix. Contact Microsoft
	Technical Support for more information.
	
	This fix has been posted to the following Internet location:
	
	  ftp://ftp.microsoft.com/bussys/exchange/exchange-public/fixes/Eng/Exchg5.0/Post-SP2-STORE/
	
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server version
	5.5. This problem has been corrected in the latest U.S. Service Pack for
	Microsoft Exchange Server version 5.5. For information on obtaining the Service
	Pack, query on the following word in the Microsoft Knowledge Base (without the
	spaces):
	
	  S E R V P A C K
	
	
	MORE INFORMATION
	================
	
	After you apply the fix described in the Status section of this article, the
	two-digit years convert to four digits according to the following table:
	
	  Two-digit year   Four-digit year
	  --------------------------------
	  00-49            2000-2049
	  50-99            1950-1999
	
	For additional information about date conversion problems with the Internet Mail
	Service, please see the following article in the Microsoft Knowledge Base:
	
	  Q173491 XFOR: Message to IMC via Telnet with Year 1900
	
	Additional query words: imail y2k
	
	======================================================================
	Keywords          : kbYear2000 kbExchange500preSP3fix 
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbZNotKeyword2
	Version           : winnt:5.0,5.5
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
