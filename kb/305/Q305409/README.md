---
layout: page
title: "Q305409: MCSE Training Kit: Designing a Microsoft Windows 2000 Network In"
permalink: /kb/305/Q305409/
---

## Q305409: MCSE Training Kit: Designing a Microsoft Windows 2000 Network In

{% raw %}

	Article: Q305409
	Product(s): Microsoft Press
	Version(s): 
	Operating System(s): 
	Keyword(s): kbdocfix kbdocerr
	Last Modified: 30-JUL-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- MSPRESS MCSE Training Kit, Designing a Microsoft Windows 2000 Network ISBN 0-7356-1133-5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article contains comments, corrections, and information about known errors
	relating to the Microsoft Press book MCSE Training Kit: Designing a Microsoft
	Windows 2000 Network Infrastructure, ISBN 0-7356-1133-5.
	
	The following topics are covered:
	
	- Page 26: Change ISO to OSI
	
	- Page 30: Change "Internet Domain" to "Interdomain"
	
	- Page 40: Incorrect Subnet ID In Figure 2.11
	
	- Page 46: Bits Should Be Bytes
	
	- Page 46: 25-bit Should Be 24-bit
	
	- Page 55: Incorrect IPSec Policy Assignment Target
	
	- Page 177: Routers Should Be Segments
	
	- Page 370: DHCP Relay Agent Should Be DHCP Server Service
	
	- Page 375: Corrections To Table 8.1
	
	- Page 376: Correction To Screened Subnet Segments
	
	- Page 415: Second Router 1 Should Be Router 2
	
	- Page 441: Incorrect Text in Diagram 9.6
	
	- Page 572: Incorrect heading
	
	- Page 573: Incorrect Number Of Simultaneous Remote Users
	
	- Page 578: Missing word "information"
	
	- Page 709: Segment B Should Be Segment A
	
	- Page 824: Missing Answer To Question 4
	
	- Page 851: Push Should Be Pull
	
	MORE INFORMATION
	================
	
	Page 26: Change ISO to OSI
	--------------------------
	
	Change the first sentence on page 26 from:
	"Your TCP/IP network protocol design focuses on the transport and network layers
	of the International Standards Organization (ISO) model."
	
	To:
	"Your TCP/IP network protocol design focuses on the transport and network layers
	of the Open-systems Interconnection (OSI) reference model."
	
	
	Page 30: Change "Internet Domain" to "Interdomain"
	--------------------------------------------------
	
	On page 30, in the 5th bulleted item, change the text from:
	"Determine the influence of Classless Internet Domain Routing (CIDR) on
	networking services designs"
	
	To:
	"Determine the influence of Classless Interdomain Routing (CIDR) on networking
	services designs"
	
	
	Page 40: Incorrect Subnet ID In Figure 2.11
	-------------------------------------------
	
	On page40, in Figure 2.11, in "Subnet Mask", change the third octet from "255" to
	"240".
	
	
	Page 46: Bits Should Be Bytes
	-----------------------------
	
	On page 46, in the first bulleted item,
	
	Change:
	"... rather than the first three bits of the IP address..."
	
	To:
	"... rather than the first three bytes of the IP address..."
	
	
	Page 46: 25-bit Should Be 24-bit
	--------------------------------
	
	On page 46, in the first bulleted paragraph, change:
	
	"25-bit"
	
	To:
	"24-bit"
	
	
	Page 55: Incorrect IPSec Policy Assignment Target
	-------------------------------------------------
	
	On page 55, under "Applying the Decision", user accounts and group accounts are
	listed as possible targets for IPSec policy assignement. This is incorrect.
	Please remove the two bullets:
	
	"User accounts
	
	Group Accounts"
	
	
	Page 177: Routers Should Be Segments
	------------------------------------
	
	On page 177, in the third bullet,
	
	Change:
	"between Routers A, B, and C"
	
	To:
	"between Segments A, B, and C"
	
	
	Page 370: DHCP Relay Agent Should Be DHCP Server Service
	--------------------------------------------------------
	
	On page 370, in the third paragraph,
	
	Change:
	"DHCP Relay Agent"
	
	To:
	"DHCP Server service"
	
	
	Page 375: Corrections To Table 8.1
	----------------------------------
	
	On page 375, in Table 8.1,
	
	in the Server B row, change "Server C" to "Server B";
	
	in the Printer A row, change "Printer C to "Printer A";
	
	and in the last two rows, change "DHPC" to "DHCP".
	
	
	Page 376: Correction To Screened Subnet Segments
	------------------------------------------------
	
	On page 376, in the last bulleted paragraph, replace the paragraph with:
	
	"Screened subnet segments
	
	Screened subnet segments (otherwise known as DMZs) exist between an
	organization's private network and the Internet. The resources in these screened
	subnets are accessed by unauthorized users. For security reasons, don't place
	DHCP servers in these screened subnets or respond to DHCP requests from Internet
	users."
	
	
	Page 415: Second Router 1 Should Be Router 2
	--------------------------------------------
	
	On page 415, in the worksheet, change the second "router 1" to "router 2".
	
	
	Page 441: Incorrect Text in Diagram 9.6
	---------------------------------------
	
	The right side of figure 9.6 on page 440 has the incorrect namespace in the
	domain parent's box. The box currently reads "contoso.msft."
	
	This should be changed to read "contoso-i.msft." to reflect the text and caption
	comments for this diagram.
	
	
	Page 572: Incorrect heading
	---------------------------
	
	On page 572, change the 2nd heading on the page from:
	"Determining the Placement of Remote Access Servers"
	
	To:
	"Determining the Number of Remote Access Servers"
	
	
	Page 573: Incorrect Number Of Simultaneous Remote Users
	-------------------------------------------------------
	
	On page 573, in the second bulleted item, change:
	"Up to 750 remote users..."
	
	To:
	"Up to 700 remote users..."
	
	
	Page 578: Missing word "information"
	------------------------------------
	
	On page 578, in the last line of the 4th text block, change:
	"the remote access clients can receive all IP configuration provided by DHCP."
	
	To:
	"the remote access clients can receive all IP configuration information provided
	by DHCP."
	
	
	Page 709: Segment B Should Be Segment A
	---------------------------------------
	
	On page 709, in the fourth bullet,
	
	Change:
	"RADIUS Server A be placed on Segment B"
	
	To:
	"RADIUS Server A be placed on Segment A"
	
	
	Page 824: Missing Answer To Question 4
	--------------------------------------
	
	On page 824, the answer to review question 4 on page 87 is missing. The missing
	answer is:
	
	"To ensure that the representatives can access the data, you can:
	
	Add additional routers to provide redundant route paths in the event of a router
	failure
	
	Add additional connections between critical segments to provide redundant route
	paths if a network segment becomes unavailable
	
	Distribute the network traffic between the additional routers and connections, to
	improve the response time of the Web-based applications."
	
	
	Page 851: Push Should Be Pull
	-----------------------------
	
	On page 851, in the fifth bulleted item,
	
	Change:
	"push"
	
	To:
	"pull"
	
	
	Microsoft Press is committed to providing informative and accurate books. All
	comments and corrections listed above are ready for inclusion in future
	printings of this book. If you have a later printing of this book, it may
	already contain most or all of the above corrections.
	
	Additional query words: TKBOOK WIN2K 0-7356-1133-5 STEEN
	
	======================================================================
	Keywords          : kbdocfix kbdocerr 
	Technology        : kbMSPressSearch
	Version           : :
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
