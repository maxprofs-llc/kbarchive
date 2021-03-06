---
layout: page
title: "Q200793: XFOR: Load Balancing Mail and Dirsync with Exchange Notes Conn."
permalink: /kb/200/Q200793/
---

## Q200793: XFOR: Load Balancing Mail and Dirsync with Exchange Notes Conn.

{% raw %}

	Article: Q200793
	Product(s): Microsoft Exchange
	Version(s): 5.5
	Operating System(s): 
	Keyword(s): exc55
	Last Modified: 21-OCT-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article provides information about how load balancing and directory
	synchronization work with the Microsoft Exchange Connector for Lotus Notes.
	
	MORE INFORMATION
	================
	
	Load Balancing
	--------------
	
	Load balancing is a method that you can use to maintain peak performance levels
	if your message traffic through the Exchange Notes Connector is high. You can
	implement load balancing by installing multiple Exchange Notes Connectors in the
	same sites. You can also use the Exchange Server route costing facilities to
	determine which messages are routed through each Exchange Notes Connector. Also
	note that load balancing operates in one direction only: from Exchange Server to
	Notes. Notes does not have a comparable feature on its site, so you cannot
	perform load balancing for traffic that is coming from the opposite direction.
	
	If you use multiple Exchange Notes Connectors for load balancing, the Notes
	server determines the route to fall back on from the Notes user's sender
	address, which indicates a path back to the Exchange Server computer. This does
	not eliminate all manual routing tasks, but it does simplify them. You also can
	configure multiple Exchange Notes Connectors, one for inbound and one for
	outbound, for load-balancing purposes. However, if you do this, replies
	typically return over the same Exchange Notes Connector that they came from in
	either direction. One alternative to this is to configure one Exchange Notes
	Connector specifically going outbound for original messages in either
	direction.
	
	The Exchange Notes Connector handles potential back ups or log jams in a message
	transfer agent (MTA) environment by immediately enacting a performance step-down
	as soon as you introduce any kind of content conversion. This is why you need to
	understand the load that the Internet Mail Service, for example, can generate.
	Multiple Exchange Notes Connectors cannot service that type of backlog. Another
	way to maintain performance is to piggyback several disconnected Notes domains
	through an Exchange Server backbone. This approach ensures that Notes users in
	Los Angeles do not communicate directly to Notes users in New York, for example.
	If you use Exchange Notes Connectors at either end of an Exchange Server
	backbone instead, you can use the Exchange Server messaging infrastructure to
	connect Notes users, even to each other.
	
	You can set up two Exchange Notes Connectors, one for mail only and another for
	directory synchronization. To do this you need two bridgehead servers on both
	the Notes side and the Exchange Server side. One pair handles mail; the other
	pair handles directory synchronization. You need proper replication in each
	environment, so that all Exchange Server users can view all the users in the
	global address list and all Notes users can view all the users in the Notes
	Address Book. This ensures that when directory synchronization takes place, more
	bandwidth is available and mail flow is not severely impacted.
	
	Directory Synchronization
	-------------------------
	
	The Exchange Notes Connector supports bi-directional directory synchronization
	with full-load or delta options. You can perform a full load or reload of the
	property page by using delta options. A full load pulls an entire directory from
	your Exchange Server or Notes site and a reload merely requests updates from
	either system. The default configuration in the current Exchange Notes Connector
	release provides the most commonly used attributes; more attributes may be added
	in subsequent releases.
	
	The current Exchange Notes Connector release also supports multiple Notes
	containers, name books, and address books. In many Notes configurations,
	particularly those that involve complex directory scenarios, users keep name
	books and address books separate. The extensive customization capabilities of
	the Exchange Notes Connector, which provide granular control of the books'
	presentation, allow users to keep name books and address books separate. The
	Exchange Notes Connector also supports Notes groups and Exchange Server
	distribution lists, and includes some filtering capabilities. For example, you
	can exclude selected Notes groups, prohibit selected groups from being moved
	into Exchange Server distribution lists, and determine which custom recipients
	are to be included in these lists.
	
	
	Additional query words: GAL dirsync
	
	======================================================================
	Keywords          : exc55 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : :5.5
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
