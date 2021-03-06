---
layout: page
title: "Q57846: Mac AL GW: Configuring the AppleLink Gateway"
permalink: /kb/057/Q57846/
---

## Q57846: Mac AL GW: Configuring the AppleLink Gateway

{% raw %}

	Article: Q57846
	Product(s): Microsoft Mail For Appletalk Networks
	Version(s): WINDOWS:2.0,2.0a,2.0b,3.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 09-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail for AppleTalk Networks, versions 2.0, 2.0a, 2.0b, 3.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Important: All Microsoft Mail version 2.00 customers who have gateways installed
	should be using the "MS Mail GW" file version 2.00b and the "Microsoft Mail
	Server" file version 2.00b, both of which are located in the System Folder of
	the Mail server. An updated "MS Mail GW" file is available through Microsoft End
	User Sales and Service at (800) 426-9400 or Microsoft International Customer
	Service at (206) 936-8661 but ONLY for customers using the AppleLink Gateway to
	Microsoft Mail. Customers using other gateways must obtain an updated "MS Mail
	GW" file from the developer of the gateway they are using. The Microsoft Mail
	server upgrade can also be obtained at the above numbers.
	
	
	The following information applies to the AppleLink gateway versions 2.0 and 3.0.
	
	Before configuring the AppleLink gateway, the AppleLink gateway must have
	previously been installed on the Microsoft Mail server by using the Gateway
	Installer program.
	
	MORE INFORMATION
	================
	
	To configure the AppleLink gateway, do the following:
	
	1. On the gateway server, sign in as Network Manager. Although you can sign in
	  as Network Manager from any Macintosh on the network, you must do the gateway
	  configuration from the gateway server because in step 4 the AppleLink gateway
	  needs to access the file "USA Modem.EF3.CCL", which must reside on the
	  gateway server.
	
	2. From the Mail menu, choose Gateway Configuration. In Mail version 3.00,
	  choose Gateway then Configuration.
	
	3. Click the icon for the AppleLink gateway.
	
	4. Click the button labeled "Connect Via". Select the file named "USA
	  Modem.EF3.CCL" and click Open. This is a Command Control Language (CCL) file
	  and is used to connect with AppleLink. Users in foreign countries may have to
	  use a modified CCL file.
	
	5. Fill in the information for the following:
	
	  a. Phone Type - Pulse (rotary) or Touch-Tone.
	
	  b. Line Speed - Baud rate of the modem being used to connect with AppleLink.
	
	  c. Network Phone # - This is usually the same number you dial when using the
	     AppleLink application to dial up AppleLink.
	
	  d. System Number - This field is already filled in for United States users.
	     Users in foreign countries usually have to change this to be the same
	     System number they use when using the AppleLink application to dial up
	     AppleLink.
	
	6. Click the Update button.
	
	Additional query words: 2.00 2.00a 2.00b 3.00
	
	======================================================================
	Keywords          :  
	Technology        : kbMailSearch kbZNotKeyword3 kbMailATN300 kbMailATN200 kbMailATN200a kbMailATN200b
	Version           : WINDOWS:2.0,2.0a,2.0b,3.0
	
	=============================================================================
	

{% endraw %}
