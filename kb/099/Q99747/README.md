---
layout: page
title: "Q99747: Connectivity Issues About SQL Server for LAN Manager"
permalink: /kb/099/Q99747/
---

## Q99747: Connectivity Issues About SQL Server for LAN Manager

{% raw %}

	Article: Q99747
	Product(s): Microsoft LAN Manager
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 30-JUL-2001
	
	SUMMARY
	=======
	
	This article summarizes some simple connectivity issues about SQL server for LAN
	Manager.
	
	MORE INFORMATION
	================
	
	1. Q. Can I install SQL server on my LAN Manager server?
	
	  A. Yes.
	
	2. Q. Can I change the name of my SQL server?
	
	  A. The SQL server name must be the same as that of your LAN Manager server. If
	  you have to change the SQL server name, you must also change the LAN Manager
	  server name.
	
	3. Q. What is a DB-LIBRARY (db-lib)?
	
	  A. It is a client-side library that provides a call-level interface for
	  clients to access SQL Server. On MS-DOS, this is a library file with a name
	  of the form "RXDBLIB.LIB," where x indicates the memory model. For example,
	  "m" for medium model and "l" for large model. On Windows, it is a medium
	  model DLL called W3DBLIB.DLL.
	
	4. Q. Can I connect my MS SQL server to work with Novell network?
	
	  A. Yes. You can do it in one of two ways:
	
	  a. Use the Novell-named pipe requestor--because Novell NetWare does not
	     natively provide named pipes, the requestor is needed for applications to
	     communicate with SQL Server using named pipes.
	
	  b. Use the NetWare Integration Kit (NIK)--the NIK makes it possible for
	     clients to communicate using NetWare's native SPX mechanism. The NIK
	     consists of a client-side net library and a server-side net manager.
	
	5. Q. Can I connect my Mac system to SQL Server?
	
	  A. Yes. You can use an SQL bridge or third party software applications by
	  TechGnosis Sequelink to interconnect with the Mac system.
	
	6. Q. What is an SQL Bridge?
	
	  A. An SQL bridge allows clients to communicate with a SQL server when the
	  client and server are using different IPC mechanisms. You can think of it as
	  a multiprotocol router. For example, it allows a Windows client using named
	  pipes as IPC to communicate with a Sybase SQL Server on UNIX using sockets as
	  IPC. SQL Bridge sits on a separate "bridge machine" that appears as an SQL
	  server to the client. The client actually connects to the bridge thinking
	  that it is the SQL server; the bridge listens to the client requests on one
	  IPC and routes them to the SQL server using another IPC. Currently, the
	  "bridge" machine needs to be running OS/2 or NT.
	
	7. Q. Does SQL Server work on a Banyan Vines network?
	
	  A. Yes. You need to buy an SQL Network Integration Kit (NIK) for Banyan Vines.
	
	8. Q. What are ODBC and ODS?
	
	  A. ODBC, or Open Database Connectivity, is a call-level interface (CLI)
	  standard that enables applications to interoperate with various DBMSs. The
	  application is written using ODBC API calls, which are translated to a
	  DBMS-specific format by modules known as ODBC drivers. Right now, drivers are
	  available for SQL Server, Oracle, and the various ISAM databases such as
	  dBASE, Paradox, Access, Btrieve, and Excel. Microsoft Access, Visual Basic,
	  FoxPro, and Excel use ODBC to achieve database connectivity.
	
	  ODS, or Open Data Services, allows you to write database "gateways." The ODS
	  API uses event driver architecture to trap SQL server client events--requests
	  such as insert, begin transmission, and so on. The ODS gateway translates
	  these events into a format understandable by another DBMS and sends it over
	  to that DBMS. So, an SQL server client thinks it is communicating with an SQL
	  server when, in reality, it is getting data from another DBMS using the
	  Gateway. Micro DecisionWare has written a gateway to get to DB/2 databases
	  using ODS. Note that ODS and ODBC can be used together because you can write
	  a gateway driver that works for all gateways.
	
	9. Q. What is ESQL?
	
	  A. ESQL, or embedded SQL, is an alternative to CLI (like db-lib and ODBC) for
	  accessing SQL server. In ESQL, the client application "embeds" SQL statements
	  within the programming language code. ESQL used to be the access method of
	  choice and is only now being replaced by CLI. For SQL server, toolkits are
	  available to write ESQL programs for COBOL and C.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	
	=============================================================================
	

{% endraw %}
