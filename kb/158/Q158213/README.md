---
layout: page
title: "Q158213: Improve LU6.2 Load Balancing if NOINITCNOS Is Used"
permalink: /kb/158/Q158213/
---

## Q158213: Improve LU6.2 Load Balancing if NOINITCNOS Is Used

{% raw %}

	Article: Q158213
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:2.0,2.1,2.11,2.11 SP1
	Operating System(s): 
	Keyword(s): 
	Last Modified: 12-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 2.0, 2.1, 2.11, 2.11 SP1 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When an APPC application tries to allocate a conversation specifying an
	LU/LU/mode partnership (using independent LU6.2), the SNA client APPC interface
	may queue the request against an SNA Server that has all available LU6.2
	sessions in use. This may happen even if an SNA Server is in the domain that may
	have a suitable LU/LU/mode partnership defined, but which has not yet completed
	Change Number of Sessions (CNOS) negotiation. This can cause an application to
	wait for an available session to become free, instead of forcing another SNA
	Server to initiate a new LU/LU session to be used by the application.
	
	Under SNA Server version 2.11, the following conditions can cause an independent
	LU 6.2 partnership to not complete CNOS negotiation:
	
	- If the NOINITCNOS registry setting is enabled on the SNA Server (this setting
	  is documented in Appendix C of the SNA Server "Reference Guide".
	
	- If the SNA Server receives an error after sending a BIND request on the Local
	  APPC LU/Remote APPC LU/SNASVCMG mode. SNA Server will log an Event 18 when
	  this occurs.
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q150959 Preventing Repeated APPC Session Activation Failures Event 18
	
	
	CAUSE
	=====
	
	If an LU-LU pair has not completed CNOS negotiation, the SNA Server was
	returning an Open(LU6.2) response error of Err1=0/Err2=1F04. This caused the SNA
	client APPC interface to try a different server for a conversation.
	
	RESOLUTION
	==========
	
	To workaround this problem, the NOINITCNOS setting should not be used.
	
	A hotfix is available for this problem, if you want to use the NOINITCNOS
	setting. The hotfix causes SNA Server to return an Err1=0/Err2=0004 to an
	Open(LU6.2) request if no CNOS negotiation has been completed for an independent
	LU/LU partnership. This causes the SNA client APPC interface to retry this
	server for a conversation, if no other servers have an available session.
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft SNA Server versions
	2.0, 2.1, 2.11, and 2.11 Service Pack 1. This problem was corrected in the
	latest Microsoft SNA Server 2.11 U.S. Service Pack. For information on obtaining
	the service pack, query on the following word in the Microsoft Knowledge Base
	(without the spaces):
	
	  S E R V P A C K
	
	
	Additional query words: sp1 prodsna
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ200 kbSNAServ211 kbSNAServ210 kbSNAServ211SP1
	Version           : WINDOWS:2.0,2.1,2.11,2.11 SP1
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
