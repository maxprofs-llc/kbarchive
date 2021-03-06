---
layout: page
title: "Q124416: Multimedia: No Sound with Soundscape Card"
permalink: /kb/124/Q124416/
---

## Q124416: Multimedia: No Sound with Soundscape Card

{% raw %}

	Article: Q124416
	Product(s): Microsoft Home Multimedia Titles
	Version(s): 1.0,Fall 1993 edition
	Operating System(s): 
	Keyword(s): 
	Last Modified: 09-NOV-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Home CD Sampler Fall 1993 edition 
	- Microsoft The Ultimate Frank Lloyd Wright for Windows, version 1.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If use a computer with an Ensoniq Soundscape sound card and run one of the
	applications listed at the top of this article, you may not hear any sound. This
	problem may occur even though sounds are played correctly with other
	Windows-based programs.
	
	RESOLUTION
	==========
	
	To correct this problem, try one of the following resolutions.
	
	Resolution 1
	------------
	
	If you are using Windows 95:
	
	If you are using Microsoft Windows 95 follow these steps to enable the Sound
	Scape secondary wave playback device:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click the Multimedia icon.
	
	3. Click the Advanced tab.
	
	4. Double-Click Audio Devices.
	
	5. In the Audio Devices window, click the Soundscape DVD MIDI,WAVE,AUX driver
	  and click the Properties button.
	
	6. Click Settings and change the Wave A setting from Disable to an available DMA
	  channel. Make sure to choose a different DMA channel than that used for the
	  DMA Channel setting. For example, if the DMA Channel setting is set to 1,
	  either 0 or 3 should work for the Wave A setting.
	
	7. Click OK and then close Control Panel.
	
	8. Quit and then restart Microsoft Windows 95.
	
	If you are using Windows 3.x:
	
	Follow these steps to enable the Soundscape secondary wave playback device in
	Windows 3.x:
	
	1. Start Windows Control Panel.
	
	2. Double-click the Drivers icon.
	
	3. In the Installed Drivers box, select the Soundscape DVD MIDI, WAVE, AUX
	  driver and then choose the Setup button.
	
	4. Change the Wave A setting from Disable to an available DMA channel. Make sure
	  to choose a different DMA channel than that used for the DMA Channel setting.
	  For example, if the DMA Channel setting is set to 1, either 0 or 3 should
	  work for the Wave A setting.
	
	5. Choose OK and then close Control Panel.
	
	6. Quit and then restart Microsoft Windows.
	
	NOTE: Some devices, such as SCSI adapter cards, can use DMA channel 0 or 3. If
	your computer has such a device, make sure to choose a different DMA channel for
	the Wave A setting
	
	Resolution 2
	------------
	
	Obtain and install the most recent Ensoniq Soundscape driver.
	
	
	MORE INFORMATION
	================
	
	The Soundscape sound card has two auxiliary wave playback devices, Wave A and
	Wave B. These devices are disabled by default. You can enable these devices
	using the steps in the "Resolution" section above. The primary wave playback
	device uses one DMA channel; use other DMA channels for the auxiliary devices.
	Note that the information in this article applies to the Soundscape Windows
	drivers version 1.52.
	
	For more information, please contact Ensoniq Product Support at (800) 942- 0096.
	
	The Ensoniq Soundscape card and drivers are manufactured by a vendor independent
	of Microsoft; we make no warranty, implied or otherwise, regarding these
	products' performance or reliability.
	
	Additional query words: ensonic 1993 multi media multimedia multi-media mmtitles
	
	======================================================================
	Keywords          :  
	Technology        : kbHomeProdSearch kbGamesSearch kbZNotKeyword kbZNotKeyword5 kbUltimateFLW kbCDSamplerF1993
	Version           : :1.0,Fall 1993 edition
	
	=============================================================================
	

{% endraw %}
