---
layout: page
title: "Q180413: TN5250 Server Uses LUs from an Incorrect SNA Server"
permalink: /kb/180/Q180413/
---

## Q180413: TN5250 Server Uses LUs from an Incorrect SNA Server

{% raw %}

	Article: Q180413
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:3.0,3.0 SP1,3.0 SP2,4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 02-APR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 3.0, 3.0 SP1, 3.0 SP2, 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The TN5250 Server on an SNA Server computer may use local and remote LUs from
	another SNA Server computer in the domain instead of the LUs defined on the SNA
	Server computer where the TN5250 Server is running.
	
	MORE INFORMATION
	================
	
	Configuration of the TN5250 Server requires local and remote LU aliases to be
	entered. If these LUs are available on the local computer, they will be used.
	However, if the LUs are not available on the local SNA Server computer (such as
	when the local SNA Server service is not started), another SNA Server computer
	in the SNA domain with the required LUs can be used. Thus, the TN5250 Server can
	be dependent on another SNA Server system in the SNA domain. Failure of either
	of these SNA Server computers causes the TN5250 Server to fail.
	
	To prevent this dependency from occurring, configure LU aliases for use by the
	TN5250 Server that are unique in the SNA domain. For example, use "local1" for
	the local LU alias on the first server, "local2" for the local LU alias on the
	second server, and so on. Note that this only applies to the local and remote LU
	aliases used by the TN5250 Server. Duplicate LU aliases must be used for the
	purpose of hot backup, as explained in Microsoft Knowledge Base Article Q128244,
	"SNA Server Load Balancing and Hot Backup."
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ300 kbSNAServ400 kbSNAServ300SP1 kbSNAServ300SP2
	Version           : WINDOWS:3.0,3.0 SP1,3.0 SP2,4.0
	Hardware          : x86
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
