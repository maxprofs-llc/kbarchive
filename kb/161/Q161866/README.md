---
layout: page
title: "Q161866: XCLN: Stopping Windows 3.x Clients from Prompting for a Domain"
permalink: /kb/161/Q161866/
---

## Q161866: XCLN: Stopping Windows 3.x Clients from Prompting for a Domain

{% raw %}

	Article: Q161866
	Product(s): Microsoft Exchange
	Version(s): WINDOWS:4.0,5.0
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 12-APR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Windows 3.x client, versions 4.0, 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The Microsoft Exchange client for Windows 3.x prompts you for a Domain Logon. If
	you don't want to be prompted for the Domain Logon, you can prevent the
	Microsoft Exchange client from prompting for it.
	
	MORE INFORMATION
	================
	
	To prevent the Microsoft Exchange client for Windows 3.x from prompting you for
	a Domain Logon, use the following steps:
	
	1. Check whether the Use Network Security During Logon option is selected. If
	  this option is selected, you will log on to the computer running Microsoft
	  Exchange Server using the same network security identity that you established
	  when you logged on to your network. Select this option if your network logon
	  identity gives you permission for your mailbox. If you clear this option, you
	  will be prompted for your logon credentials when you start the Microsoft
	  Exchange client. You can view the state of this option by doing the
	  following:
	
	  a. Start the Microsoft Exchange client.
	
	  b. On the Tools menu, click Services.
	
	  c. Select the Microsoft Exchange Server service.
	
	  d. Click the Properties button.
	
	  e. Click the Advanced tab.
	
	2. Check whether you have a password list (.pwl) file. In Windows for
	  Workgroups, password caching is a feature that maintains a list of the
	  passwords that you have used, and the resources to which they apply.
	  Passwords are saved and retrieved transparently to you. The password cache
	  enables the restoration of connections to shared resources when you log on.
	  This file should exist in the Windows directory, and appear as Username.pwl.
	  If it does exist, it may be corrupted. Create a new one by deleting the old
	  file and restarting both Windows for Workgroups and the Microsoft Exchange
	  client. This will create a new .pwl file, so you should test it again.
	
	3. Check whether real-mode IPX/SPX is your only network protocol. Real-mode
	  IPX/SPX does not support named pipes, and this support is needed to make
	  authenticated remote procedure calls (RPCs). If this is your only protocol,
	  you must use a .pwl file to eliminate the domain logon prompt.
	
	4. Check whether any of your installed protocols support named pipes. Again,
	  named pipe support is required for authenticated RPCs. If none of your
	  protocols support named pipes, you must use a .pwl file.
	
	5. Check whether named pipes is first in the binding order. When the Microsoft
	  Exchange client is installed, it sets the default RPC binding order that
	  determines the order of network protocols that RPC attempts to bind over. If
	  named pipes is first, verify that the Rpc16c1.dll file is present on the
	  computer, make sure that the computer running Microsoft Exchange Server
	  supports named pipes, and test it using Rping.exe. For more information about
	  the RPC Ping troubleshooting tool, please refer to the Microsoft Exchange
	  Administrator's Guide. If named pipes is not first, you can change the order
	  on this computer by editing the Exchng.ini file in the Windows directory. For
	  future installations from a network installation point, a Microsoft Exchange
	  administrator can use the Microsoft Exchange Setup Editor to change the
	  default binding order.
	
	Additional query words: exclnfaqold
	
	======================================================================
	Keywords          : kbusage 
	Technology        : kbExchangeSearch kbExchange500 kbExchange400 kbExchangeClientSearch kbZNotKeyword3
	Version           : WINDOWS:4.0,5.0
	
	=============================================================================
	

{% endraw %}
