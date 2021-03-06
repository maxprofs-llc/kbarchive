---
layout: page
title: "Q198410: Microsoft DNS Server Registry Parameters, Part 3 of 3"
permalink: /kb/198/Q198410/
---

## Q198410: Microsoft DNS Server Registry Parameters, Part 3 of 3

{% raw %}

	Article: Q198410
	Product(s): Microsoft Windows NT
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SUMMARY
	=======
	
	This article consists of 3 parts and describes settings for the Microsoft Domain
	Name Service (DNS) server. You can modify most settings using the DNSADMIN tool,
	although some settings can only be altered using Registry Editor.
	
	For additional information, please see the following articles in the Microsoft
	Knowledge Base:
	
	  Q198408 Microsoft DNS Server Registry Parameters, Part 1 of 3
	
	  Q198409 Microsoft DNS Server Registry Parameters, Part 2 of 3
	
	MORE INFORMATION
	================
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	To change these parameters, use the following procedure:
	
	1. Start Registry Editor (Regedt32.exe).
	
	2. From the HKEY_LOCAL_MACHINE subtree, go to the following key:
	
	    <B>SYSTEM\CurrentControlSet\Services </B>
	
	3. From the Edit menu, click Add Value and add a value to the key described in
	  the appropriate entry below. Type in the value, and use the "Data Type" check
	  box to set the value type.
	
	4. Click OK.
	
	5. Quit Registry Editor.
	
	6. Restart the DNS server for the above changes to take affect.
	
	Server Parameters
	-----------------
	
	Several registry parameters determine behavior of the entire server. Each of
	these is a registry value under
	
	  HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\DNS\Parameters
	
	NOTE: These registry keys are read only at startup. Some may be reset and, in
	some cases, the server behavior dynamically changed, through the DNS
	Administrator. But if manually reset, the DNS server must be restarted to pick
	up the new value.
	
	SendOnNonDnsPort
	----------------
	
	  Value:      SendOnNonDnsPort
	  Added:    SP4 (April 1998)
	  Type:     DWORD
	  Default:  NoKey  (Send on DNS port - 53)
	  Function: Determines port on which server sends UDP queries to other DNS
	            servers.
	
	By default, the DNS server sends queries to other DNS servers on a socket bound
	to the DNS port. Sometimes this situation is NOT desirable. The most obvious
	case being when an admin firewalls off the DNS port, to prevent outside access
	to the DNS server, but still wants the DNS server to be able to contact Internet
	DNS servers to provide Internet name resolution for internal clients. This is
	also desirable if the server is serving disjoint nets (see discussion below for
	DisjointNets key). Setting the SendOnNonDnsPort key to a non-zero value, causing
	the DNS server to bind to an arbitrary port for sending to remote DNS servers.
	If the SendOnNoDnsPort value is set >1024, then the DNS server will bind
	explicitly to the port value given. This is useful is the admin wants to fix the
	port for firewalling purposes.
	
	Examples:
	
	  SendOnNonDnsPort missing or 0 => sends to other DNS servers come from
	  port 53.
	
	  SendOnNonDnsPort = 1 => sends come from arbitrary port.
	
	  SendOnNonDnsPort = 2000 => sends comes from port 2000.
	
	DisjointNets
	------------
	
	  Value:      DisjointNets
	  Added:    SP2
	  Type:     DWORD (Boolean)
	  Default:  NoKey  (Version dependent see below)
	  Function: Allows override of default  binding for socket used to send
	            queries to remote servers.
	
	Resolver behavior dictates that DNS servers bind explicitly to IP addresses (see
	discussion in ListenAddresses above). This, in turn, means that there is a
	tradeoff in determining the binding of the socket used to query remote DNS
	servers. The binding must be such that the remote server can respond to the
	address in the IP source address of the query.
	
	If there is a single IP address for the computer running the DNS server, there is
	no problem. However if the computer is multihomed, a problem may arise as the
	send socket may have be chosen in one of two ways:
	
	1. Bind send socket to INADDR_ANY.
	
	  In this case, the TCP/IP stack determines the IP source address when the query
	  is sent to the remote DNS. This is ideal in that the stack will always choose
	  the IP source address of the adapter the packet is sent on and, hence, the IP
	  address will be reachable when the remote DNS sends back. However, it means
	  that the DNS server MUST be listening on the address the stack chooses. If
	  the server is configured to only listen on some of the IP addresses on the
	  computer, problems may arise.
	
	2. Use one of the DNS listen sockets as send socket.
	
	  In this case, the packet is always sent with a source IP that corresponds to
	  one of the DNS listen addresses. Unfortunately, this IP may not be on the
	  adapter the stack must send on to reach the remote DNS server. And in this
	  case, when the remote DNS server attempts to respond, it may not have a route
	  back to this IP. This would happen when the DNS server has "Disjoint Nets";
	  in other words, it is attached to two (or more) networks that are not
	  otherwise connected. This is the classic case of the DNS server sitting on a
	  firewall or proxy server.
	
	The DisjointNets registry key allows override of default server behavior, forcing
	sends on socket bound to INADDR_ANY (method 1 above). If the DisjointNets
	registry key exists and is nonzero, a send socket is created bound to
	INADDR_ANY. If the DisjointNets registry key does not exist or is zero, the
	default server behavior occurs.
	
	Default server behavior (Service Pack 3 and later):
	
	- Single DNS IP, use the listen socket for send also.
	
	- Multihomed, all addresses in use by DNS (or DisjointNets set) use INADDR_ANY
	  socket.
	
	- Multihomed, all addresses not in use by DNS, use first listen IP's socket as
	  send socket.
	
	Note that, in the case where the computer has multiple IP addresses and they are
	not all in use by DNS, there is no guarantee of correct behavior in the disjoint
	net case. The DisjointNets key can be turned on to force use of method 1, but
	there is no guarantee that the stack will always select an IP address that the
	DNS server is listening on. If using the DNS server on two disjoint nets (for
	example, on a firewall), configure the computer with only a small number of IP
	addresses and let DNS run on them all (that is, do NOT configure
	ListenAddresses).
	
	
	DisableAutoReverseZones
	-----------------------
	
	  Value:      DisableAutoReverseZones
	  Added:    Windows NT 4.0
	  Type:     DWORD (Boolean)
	  Default:  NoKey  (Create automatic reverse-lookup zones)
	  Function: Determine whether server automatically creates standard
	            reverse lookup zones.
	
	Every DNS server should (according to RFC) be authoritative for three reverse
	lookup zones:
	
	- 0.in-addr.arpa.
	
	- 127.in-addr.arpa.
	
	- 255.in-addr.arpa
	
	The reason for this is that clients sometimes query for standard IP addresses
	such as 0.0.0.0, 127.0.0.1 (loopback), and 255.255.255.255 (broadcast). By being
	authoritative for the zones corresponding to these queries, the DNS server
	avoids unnecessary recursions to the root servers on these queries.
	
	If the DisableAutoReverseZones key does not exist or is zero, the Microsoft DNS
	server will automatically create these zones with the correct entries (none
	except for a PTR for 127.0.0.1 to localhost).
	
	If DisableAutoReverseZones is nonzero, the server does NOT create these zones.
	
	AutoCacheUpdate
	---------------
	
	  Value:      AutoCacheUpdate
	  Added:    Windows NT 4.0
	  Type:     DWORD (Boolean)
	  Default:  NoKey  (Do automatic cache updates)
	  Function: Determine whether server attempts to update cache entries
	            using data from root servers.
	
	When a DNS server starts, it needs a list of root server "hints" -- NS and A
	records for the servers, historically called the cache file. Traditionally DNS
	administrators could keep this file current by downloading a new copy from the
	InterNIC. This method works adequately when the root servers stay fairly static,
	but does require attention on the part of the administrator when updates and
	changes are made (for example, the massive renaming in late 1995).
	
	The Microsoft DNS server has a feature to allow the server to attempt to write
	back a new cache file based on the response from the root servers.
	
	If the AutoCacheUpdate key does NOT exist or is nonzero, the Microsoft DNS server
	will rewrite the cache file based on the data received from querying the root
	DNS servers on startup.
	
	If the key is zero, the DNS server does not do this update.
	
	
	CleanupInterval
	---------------
	
	  Value:      CleanupInterval
	  Added:    Windows NT 4.0
	  Type:     DWORD
	  Default:  NoKey (Interval is one hour)
	  Function: Set interval between successive cleanup walks of DNS database.
	
	NOTE: The CleanupInterval Registry Key is not available in Win2k.
	
	Periodically, the DNS server wakes up a thread to walk the database and eliminate
	cached records and nodes, which have timed out. (The only purpose is to recover
	the memory.) The thread will also check the authoritative zones and write back
	any that are "dirty" -- have records from administrative update that have NOT
	been written back to database file.
	
	The value of this key is the interval between wakeups of the cleanup thread in
	seconds. If the key does not exist, the default is one hour. There is no
	particular reason to change this value, although in a memory unconstrained
	situation, a longer wakeup (possibly a day) might slightly improve performance.
	In a memory constrained environment, shorter intervals are desirable, but making
	them very short (such as a few minutes) would cause excessive cycles to be
	wasted on this timeout thread.
	
	StrictFileParsing
	-----------------
	
	  Value:      StrictFileParsing
	  Added:    SP4
	  Type:     DWORD (Boolean)
	  Default:  NoKey (after SP4 non-strict)
	  Function: Set server to parse files strictly.
	
	BIND implementations have generally been liberal about allowing non-RFC compliant
	records in zone files. Among the errors allowed:
	
	- Records for names outside of the zone.
	
	- CNAME records at names that contain other records (and vice versa).
	
	When BIND files with bad data are moved over to a Microsoft DNS server, the
	server would fail to start, and individuals who were not aware that the
	explanations were in the event log, were out of luck. Starting with Service Pack
	4, the server will, by default, log and ignore zone file errors, so the server
	can start.
	
	If the StrictFileParsing key does not exist or is zero, the server will log and
	ignore bad data in file and continue to load. If the StrictFileParsing is
	nonzero, the server will log and fail on zone file errors.
	
	Zone Registry Keys
	------------------
	
	Several registry parameters determine behavior of the individual zones. Each of
	these is a registry value under the following key:
	
	  HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services
	  \DNS\Zones\<Zone_Name>
	
	NOTE: The above registry key is one path; it has been wrapped for readability.
	
	This key, in turn, contains a registry key for each authoritative zones and, if
	not root authoritative, one for the cache (key name "."). This section discusses
	registry parameters that determine behavior specific to individual zones. Each
	of these registry parameters is found under a registry key for the name of the
	zone it applies to.
	
	NOTE: These registry keys are read only at startup. Some may be reset and the
	server behavior dynamically changed through the DNS Administrator. But, if
	manually reset, the DNS server MUST be restarted to pick up the new value.
	
	Type
	----
	
	  Value:      Type
	  Added:    Windows NT 4.0
	  Type:     DWORD
	  Default:  None (Key must exist)
	  Function: Determines zone type.
	
	The Type registry key determines type of zone when starting from the registry.
	Zone types mappings are:
	
	  0  cache (root hint) file
	  1  primary zone
	  2  secondary zone
	
	The Type registry key is read to determine the type of zone on registry startup.
	If it is deleted or invalid, the server will fail to start. Therefore, do NOT
	edit this key. To change the zone type, use the DNS Administrator Zone
	properties, General dialog box.
	
	NOTE: If starting from a boot file, this key is ignored and overwritten with zone
	type specified in the boot file.
	
	UseDatabase
	-----------
	
	  Value:      UseDatabase
	  Added:    Windows NT 4.0
	  Type:     DWORD (Boolean)
	  Default:  0 (Do not use database)
	  Function: None
	
	The UseDatabase registrykey is unused.
	
	
	DatabaseFile
	------------
	
	  Value:      DatabaseFile
	  Added:    Windows NT 4.0
	  Type:     STRING
	  Default:  None (Key must exist)
	  Function: Determines zone's database file.
	
	The DatabaseFile registry key gives the name of the zone's database file (if
	any). When starting from the registry, this key determines the file that is read
	to load the zone. This key MUST exist for primary zones. Secondary zones may be
	configured to not load from a zone file. Do not edit this key. To change the
	zone file, use the DNS Administrator Zone properties, General dialog box.
	
	NOTE: If starting from a boot file, this key is ignored and overwritten with zone
	file specified in the boot file.
	
	MasterServers
	-------------
	
	  Value:      MasterServers
	  Added:    Windows NT 4.0
	  Type:     BINARY
	  Default:  None (Key must exist for secondaries)
	  Function: Determines master servers a secondary should contact for zone
	            transfer.
	
	Secondaries for a zone must have a list of servers that they can query to receive
	information to determine current zone version and to receive zone transfers
	from, if necessary. The MasterServers key is a list of IP addresses of masters
	for the given zone. The list is not dotted IP strings, but a counted array of
	raw IP addresses in net byte order. It should be configured through the Zone
	Properties, General dialog box in the Administrator tool. Editing the registry
	key is discouraged.
	
	NOTES:
	
	- When using registry boot, the DNS server reads the MasterServers key for a
	  secondary zone on startup. If the MasterServers key does not exist, or is
	  invalid, the DNS server will not start.
	
	- If starting from a boot file, this key is ignored and overwritten with the
	  master IP list specified in the boot file.
	
	SecondaryServers
	----------------
	
	  Value:      SecondaryServers
	  Added:    Windows NT 4.0
	  Type:     BINARY
	  Default:  NoKey (No secondary list)
	  Function: Determines secondary servers for to notify or limit transfers
	            to.
	
	The Microsoft DNS server allows specification of a secondary server list. Note
	that it is a list of secondaries for this zone on this server. It need not be a
	complete list of secondaries for the zone. Its purpose is to give administrators
	a fine degree of control over the replication graph for a zone.
	
	This list has two functions:
	
	- Servers in this list are notified when a new version of the zone is
	  available.
	
	- If the SecureSecondaries registry key (see below) is used, zone
	
	transfers are refused to servers not in this list.
	
	The SecondaryServers key is not a list of dotted IP strings, but a counted array
	of raw IP addresses in net byte order. It should be configured through the Zone
	Properties, Notify dialog box in the administrator tool. Editing the registry
	key is discouraged. Especially, do NOT delete this registry key to attempt to
	create an empty secondary list.
	
	
	SecureSecondaries
	-----------------
	
	  Value:      SecureSecondaries
	  Added:    Windows NT 4.0
	  Type:     DWORD (Boolean)
	  Default:  NoKey (No secondary security)
	  Function: Sets security on zone transfer requests.
	
	The Microsoft DNS server allows limitation of zone transfers to a select list
	(possibly empty) of servers. This is useful for two reasons:
	
	- Keeps information about zones private. Complete zone information can be
	  useful in choosing targets for security attacks. By limiting information, the
	  process of learning about potential targets is more difficult and time
	  consuming, making the barrier against attack incrementally higher.
	
	- Saves CPU cycles and prevents denial of service attacks. Zone transfer for a
	  large zone is an expensive operation. Therefore, it is desirable to limit it
	  to requests from servers that require it for a legitimate purpose.
	
	If the SecureSecondaries registry key is nonzero, zone transfer is limited to
	requests from IP addresses given in the SecondaryServers registry key (see
	above). If the SecondaryServers registry key list is empty, no transfers are
	sent for this zone. This key may be reset through the Zone Properties, Notify
	dialog box.
	
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : :4.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
