---
layout: page
title: "Q175249: Extra Modem Settings R-T for Connecting to MSN"
permalink: /kb/175/Q175249/
---

## Q175249: Extra Modem Settings R-T for Connecting to MSN

{% raw %}

	Article: Q175249
	Product(s): The Microsoft Network
	Version(s): WINDOWS:1.3,2.0,2.5
	Operating System(s): 
	Keyword(s): kbmsnkbfaq
	Last Modified: 08-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Network versions 1.3, 2.0, 2.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	You may be unable to connect, or have difficulty remaining connected to MSN, The
	Microsoft Network. Some modems may require extra settings or specific
	configurations to connect to MSN.
	
	The following table lists extra modem settings and configurations that may help
	specific modems connect.
	
	NOTE: Rockwell settings may work for any modem that uses the Rockwell chipset,
	including Boca, Zoltrix, and Zoom 14.4 modems.
	
	MORE INFORMATION
	================
	
	Manufacturer/Model      Extra Settings    Status       Configuration
	---------------------------------------------------------------------------
	
	Rockwell 14.4 V1.403    AT&F or &Q6&K3    CONFIRMED    Install as a
	                                                      Standard 14.4
	                                                      Data/Fax. Error
	                                                      Control off.
	
	Rockwell 14.4 V1.510    AT&F or &Q6&K3    CONFIRMED    Install as a
	                                                      Standard 14.4
	                                                      Data/Fax. Error
	                                                      Control off.
	
	Rockwell 14.4 V1.620    AT&F or \N0&K3    CONFIRMED    Install as a
	                                                      Standard 14.4
	                                                      Data/Fax. Error
	                                                      Control off.
	
	Rockwell 14.4 Data/Fax  Unknown           UNCONFIRMED  Install as a
	                                                      Standard 14.4
	                                                      Data/Fax.
	
	Rockwell V2.00          &Q6&K3 or \N0&K4  UNCONFIRMED  None.
	
	Rockwell 28.8dpi        S7=90S10=80       UNCONFIRMED  Use the extra
	                                                      settings to stop
	                                                      dropped connection
	                                                      issues.
	
	Sierra SQ3228           AT&F              UNCONFIRMED  Error Control off.
	
	Sierra SQ3465           AT&F              UNCONFIRMED  Error Control off.
	
	Sierra 28.8             AT&FX4&C1&D2E1    UNCONFIRMED  None.
	
	Sierra 28.8 PnP         AT&H4             CONFIRMED    (ATI3=16550*ext-
	Data/Fax/Voice                                         hyp-V34.4)
	
	Supra (All Modems)      Unknown           UNCONFIRMED  If Fax Talk, a
	                                                      program that is
	                                                      provided with all
	                                                      Supra modems, has
	                                                      been installed,
	                                                      you must remove
	                                                      this program
	                                                      to be able to
	                                                      connect to the
	                                                      Internet & MSN
	                                                      service type.
	
	Supra 28.8i PnP         AT&D0             CONFIRMED    Error Control off.
	                                                      Compress Data off.
	                                                      Maximum speed set
	                                                      to 57600.
	
	Supra 28.8I PnP         AT&F1&D0          UNCONFIRMED  Error Control Off.
	Supra Express 28.8 PnP                                 Maximum speed set
	                                                      to 57600.
	
	Supra Diamond           AT&F1             CONFIRMED    Install as a
	Express 33.6                                           Standard 28.8
	                                                      Data/Fax.
	
	Toshiba 14.4 PCMCIA     AT&F              UNCONFIRMED  None.
	
	To add an extra setting or to change the Use Error Control or Compress Data
	options, use the following steps:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click Modems.
	
	3. Click the modem you are using, and then click Properties.
	
	4. On the Connection tab, click Advanced.
	
	5. In the Extra Settings box, type the appropriate extra settings.
	
	6. Enable or disable the Use Error Control and Compress Data options as
	  appropriate.
	
	7. Click OK or Close until you return to Control Panel.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbmsn kbfaq
	Technology        : kbMSNSearch kbMSN200 kbMSN130 kbMSN250
	Version           : WINDOWS:1.3,2.0,2.5
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
