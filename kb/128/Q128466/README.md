---
layout: page
title: "Q128466: PROFS: Multiple Attachments Generated by Host Access"
permalink: /kb/128/Q128466/
---

## Q128466: PROFS: Multiple Attachments Generated by Host Access

	Article: Q128466
	Product(s): Microsoft Mail For PC Networks
	Version(s): 3.4a
	Operating System(s): 
	Keyword(s): 
	Last Modified: 26-APR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail Gateway to IBM PROFS and OfficeVision, version 3.4a 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you send an attachment from the local area network (LAN) to a DISOSS type
	host, PROFS Host Access generates multiple attachments.
	
	CAUSE
	=====
	
	When you send LAN-based messages with attachments to a DISOSS type host (this
	includes SoftSwitch-based gateways and IBMMAIL), and those messages are
	consistent with LAN_HOST DATA table DOC=N, an additional attachment is generated
	and sent using the CMS SENDFILE command. This additional attachment can result
	in an error message to the LAN, or these additional messages can accumulate in
	the RSCS RDR or the MVS JES queue.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in version 3.4a of Microsoft Mail
	Gateway to PROFS. This problem was corrected in PWAATTS.XED version 3.4a.041. If
	you do not have version 34a.041, you can find PWAATTS.EXE, a self-extracting
	file, on the following services:
	
	- Microsoft's World Wide Web Site on the Internet
	
	  On the www.microsoft.com home page, click the Support icon.
	  Click Knowledge Base, and select the product.
	  Enter kbfile PWAATTS.EXE, and click GO!
	  Open the article, and click the button to download the file.
	
	- Internet (anonymous FTP)
	
	  ftp ftp.microsoft.com
	  Change to the Softlib/Mslfiles folder.
	  Get PWAATTS.EXE
	
	- The Microsoft Network
	
	  On the Edit menu, click Go To, and then click Other Location.
	  Type "mssupport" (without the quotation marks).
	  Double-click the MS Software Library icon.
	  Find the appropriate product area.
	  Locate and Download PWAATTS.EXE.
	
	
	For additional information about downloading, please see the following article in
	the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	
	Additional query words: 3.40a
	
	======================================================================
	Keywords          :  
	Technology        : kbMailSearch kbMailGateSearch kbZNotKeyword3 kbMailGateIBMPROFS340a
	Version           : :3.4a
	
	=============================================================================
	