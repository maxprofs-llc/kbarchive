---
layout: page
title: "Q229812: XCLN: Can't Check Attendee Availability from Resource Calendar"
permalink: /kb/229/Q229812/
---

## Q229812: XCLN: Can't Check Attendee Availability from Resource Calendar

{% raw %}

	Article: Q229812
	Product(s): Microsoft Exchange
	Version(s): ; WINDOWS:
	Operating System(s): 
	Keyword(s): 
	Last Modified: 22-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Outlook 97, on platform(s):
	   - the operating system: Microsoft Windows NT 
	- Microsoft Outlook 98, on platform(s):
	   - the operating system: Microsoft Windows NT 
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you use Resource accounts and delegates, you cannot check the availability
	of attendees for a scheduled meeting from within the Resource Calendar.
	
	MORE INFORMATION
	================
	
	The attendee list that you see when opening a meeting request is built from the
	recipients of the message. The To recipients of the message are considered the
	"Required" attendees and the Cc recipients are the "Optional" attendees.
	
	In the case of the delegate, meeting requests are forwarded by a server rule from
	the resource mailbox to the delegate mailbox. As with any forwarded message, the
	original recipients of the message are not retained, so that information is
	lost. Outlook 97 avoided this by storing the names of the original recipients in
	the meeting request, and these names are displayed in the meeting attendee list.
	However in Outlook 98, the delegate receives only the attendee names and not all
	the information normally available for a message recipient, so the delegate is
	unable to look up the attendees' free/busy times.
	
	
	Additional query words: 8.0 8.01 8.02 8.03 8.04 8.5
	
	======================================================================
	Keywords          :  
	Technology        : kbOutlookSearch kbOutlook97Search kbZNotKeyword3
	Version           : :; WINDOWS:
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
