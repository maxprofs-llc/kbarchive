---
layout: page
title: "Q139351: STOP Msg: c000021a - Using Mandatory Profile w/o Access Rights"
permalink: /kb/139/Q139351/
---

## Q139351: STOP Msg: c000021a - Using Mandatory Profile w/o Access Rights

{% raw %}

	Article: Q139351
	Product(s): Microsoft Windows NT
	Version(s): winnt:3.51
	Operating System(s): 
	Keyword(s): kbother
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 3.51 
	- Microsoft Windows NT Server version 3.51 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Create a user account and specify that it should use a mandatory profile. Create
	the mandatory profile but do not specify that the user just created should be
	allowed to use it.
	
	When you log in, using an account that attempts to use a mandatory profile it
	does not have privilege for, an error message appears (correctly) saying you
	cannot logon as the account does not have access rights to the profile. However
	a few seconds later, the following STOP message appears:
	
	  STOP: c000021a
	
	CAUSE
	=====
	
	During logon processing, Winlogon detects the account does not have access
	rights to the mandatory profile assigned to that user. Because the user is not
	allowed to login without a valid mandatory profile, logoff processing is
	initiated. During this logoff processing, Windows NT attempts to reference the
	mandatory profile, which fails because the mandatory profile was never loaded in
	the first place and this causes a memory access violation which results in the
	STOP Message.
	
	RESOLUTION
	==========
	
	This problem has been corrected in the latest Service Pack for Windows NT
	version 3.51.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT version 3.51. This
	problem was corrected in the latest Windows NT 3.51 U.S. Service Pack and
	Windows NT 4.0. For information on obtaining the Service Pack, query on the
	following word in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	
	Additional query words: prodnt upedit man usrmgr
	
	======================================================================
	Keywords          : kbother 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNT351search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS351 kbWinNTS351search
	Version           : winnt:3.51
	
	=============================================================================
	

{% endraw %}
