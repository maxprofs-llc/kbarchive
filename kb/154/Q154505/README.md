---
layout: page
title: "Q154505: XFOR: SMTP Protocol Log Not Created When Minimally Logging"
permalink: /kb/154/Q154505/
---

## Q154505: XFOR: SMTP Protocol Log Not Created When Minimally Logging

	Article: Q154505
	Product(s): Microsoft Exchange
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 15-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Enabling Minimum Logging level on the Internet Mail Connector for SMTP Protocol
	Log does not create an L0000000.LOG and an Event ID of 2004 is never written to
	the Application event log.
	
	WORKAROUND
	==========
	
	Change the Logging level to Medium or higher will generate an SMTP Protocol log
	and generate Event ID 2004.
	
	MORE INFORMATION
	================
	
	Page 578, Chapter 17 of the Microsoft Exchange Server Administrator's Guide
	incorrectly states the following regarding Minimum logging: Logging SMTP
	Information
	
	SMTP events are generated by the connections of an Internet Mail Connector. When
	you increase the diagnostics logging level for the SMTP Protocol Log category,
	Microsoft Exchange Server writes these events to text files. Each concurrent
	connection logs its events to a separate file. You can find these files in
	\EXCHSRVR\IMCDATA\LOG.
	
	TIP: A quick way to tell if SMTP logging is enabled is to check the Windows NT
	application event log when the Internet Mail Connector is started. If enabled,
	event 2004 is written to the event log. To locate this event in the Event
	Viewer, search the application event log for ID, or the source, MSExchangeIMC,
	and the category, SMTP Protocol Log, of the event.
	
	The headers and body of outgoing messages cannot be logged. However, the entire
	text of incoming messages is included.
	
	1. Select the Diagnostics Logging tab.
	
	2. Select SMTP Protocol Log.
	
	3. Select a logging level.
	
	4. Restart the Internet Mail Connector.
	
	  Option        Description
	
	  None    (0)  No text logs are created. This is the default.
	  Minimum (1)  Connection information is written to the SMTP log.
	  Medium  (3)  SMTP commands and headers are written to the SMTP log.
	  Maximum (5)  Complete, unformatted protocol packets are written to the
	  SMTP log.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in version 4.0 of Microsoft
	Exchange. We are researching this problem and will post new information here in
	the Microsoft Knowledge Base as it becomes available.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbusage 
	Technology        : kbExchangeSearch kbExchange400 kbZNotKeyword2
	Version           : :4.0
	
	=============================================================================
	