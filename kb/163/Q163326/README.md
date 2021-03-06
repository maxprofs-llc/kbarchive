---
layout: page
title: "Q163326: XCON: How and Why to Run Mtacheck"
permalink: /kb/163/Q163326/
---

## Q163326: XCON: How and Why to Run Mtacheck

{% raw %}

	Article: Q163326
	Product(s): Microsoft Exchange
	Version(s): winnt:4.0,5.0,5.5
	Operating System(s): 
	Keyword(s): kbusage exc4 exc5 exc55
	Last Modified: 19-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 5.5, 4.0, 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Mtacheck Logs are text files that show the results of running the Mtacheck.exe
	utility. The Mtacheck utility scans the internal database of the Microsoft
	Exchange Message Transfer Agent (MTA) looking for objects that are damaged and
	may be interfering with the queue processing. It places defective objects from
	the queues in files for you to examine later. In addition, Mtacheck rebuilds the
	queues so the MTA can be restarted and return to processing.
	
	MORE INFORMATION
	================
	
	Mtacheck can be run manually, but is also run automatically when the MTA service
	determines that the MTA was not shut down gracefully. If an automatic Mtacheck
	is run, events will be logged to the Windows NT Application Event Log and an
	Mtacheck.log file will be generated in the Mtacheck.out sub-directory of the
	exchsrvr\MTADATA directory containing the DB*.DAT files used by the MTA. If the
	Microsoft Exchange Performance Optimizer has been used to move Mtadata files,
	there may be more than one Mtadata directory).
	
	If Mtacheck is run manually, no logging is performed unless specified on the
	command line. In addition, logs can be created in any location and with any
	name. In terms of logging, the automatic Mtacheck is the equivalent of running
	the following at the command line (except an automatic run also logs events to
	the event logs):
	
	  MTACHECK /V /F \exchsrvr\mtadata\Mtacheck.out\Mtacheck.log
	
	INTERPRETING MTACHECK OUTPUT
	----------------------------
	
	Mtacheck examines each queue in the database. If it finds an error, it reports
	the name of the queue, the type of error, and the number of messages returned to
	the rebuilt queue.
	
	For example:
	
	  Queue 'xxxxxxx' required reconstruction
	   - corrupted queue file
	  23 messages recovered to the queue
	
	It then examines objects in the queues. If an object is in error, it removes it
	from the queue and places it in Exchsrvr\mtadata\mtacheck.out. It reports the
	object ID, error type, queue name, and the MTS-ID of the corrupted message, if
	known.
	
	An MTS-ID is assigned to each message by its transport service and remains with
	the message to its destination, although gateways may assign additional
	identifiers. It consists of the originating server, the date and time the
	message was sent, and a unique hexadecimal identifier for the message.
	
	A sample Mtacheck log can include:
	
	   Object 300596 invalid
	   - missing object file
	  Object removed from queue 'xxxxxxx'
	  MTS-ID: c=US;a= ;p=Owen;l=Washington0196012020010800000CDE
	
	When the MTA finishes processing, it displays one of following messages to
	describe the results:
	
	- Database clean, no errors detected
	
	- Database repaired, some data may have been lost
	
	- <number> queue(s) required repair out of <percent> detected
	
	- <number> object(s) damaged out of <percent> detected
	
	- Database has serious errors and cannot be reconstructed.
	
	- Some objects missing from the Boot Environment. Please reload the files from
	  the BOOTENV directory on the install CD.
	
	The boot environment message indicates that the report templates and other
	objects the MTA needs are missing and the MTA cannot generate them. These
	objects are included in the files in the \BOOTENV directory. Once you have
	installed them, rerun Mtacheck. When the process is complete, restart the MTA.
	
	Warning: Copy only objects that are missing. If you replace existing objects, all
	messages in MTA queues will be deleted.
	
	SEARCHING MESSAGE LOGS BY MESSAGE ID
	------------------------------------
	
	Mtacheck also reports the message ID of removed objects in its log if they can be
	determined. If message tracking is enabled, you can search the tracking log for
	the object by its message ID. Determining the path of the bad message can lead
	you to the cause of the problem. You may need to search the logs of more than
	one site to find the complete path of the message.
	
	Additional query words: whitepaper logging section
	
	======================================================================
	Keywords          : kbusage exc4 exc5 exc55 
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbExchange400 kbZNotKeyword2
	Version           : winnt:4.0,5.0,5.5
	
	=============================================================================
	

{% endraw %}
