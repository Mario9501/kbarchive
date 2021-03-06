---
layout: page
title: "Q175248: Extra Modem Settings N-P for Connecting to MSN"
permalink: /kb/175/Q175248/
---

## Q175248: Extra Modem Settings N-P for Connecting to MSN

{% raw %}

	Article: Q175248
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
	specific modems connect to MSN.
	
	NOTE: Rockwell settings may work for any modem that uses the Rockwell chipset,
	including Boca, Zoltrix, and Zoom 14.4 modems.
	
	MORE INFORMATION
	================
	
	Manufacturer/Model       Extra Settings   Status       Configuration
	---------------------------------------------------------------------------
	
	NEC 14.4 Data/Fax        AT&F             UNCONFIRMED  Error Control on.
	                                                      Compress Data off.
	
	NEC 28.8 Data/Fax        AT&F1            CONFIRMED    Error Control on,
	                                                      Compress Data off.
	
	NEC 28.8 V.34 FDVSP PNP  AT&F1            UNCONFIRMED  Error Control off.
	
	NewCom 28.8              AT&F1            UNCONFIRMED  (ATI3=v1.300/v34_dp)
	
	Ositech 28.8 PCMCIA      None             CONFIRMED    Error Control
	                                                      off. Accept the
	                                                      Windows 95
	                                                      detection settings.
	
	Packard Bell 28.8        AT&F1            CONFIRMED    Error Control on.
	Data/Fax                                               Compress Data off.
	
	Packard Bell 14.4        AT&F1            UNCONFIRMED  Set maximum speed
	Data/Fax/Voice                                         to 38400.
	
	Packard Bell 28.8        AT&F1            CONFIRMED    Error Control on.
	Data/Fax/Voice                                         Compress Data off.
	
	PCTEL/HSP 33.6 Deluxe    AT&F&C1&D2&K3&W1 CONFIRMED    Reduce modem
	                                                      speed to 33600.
	                                                      Error Control
	                                                      off.
	
	Phoebe 28.8              \Q3\N3\J0%C0     CONFIRMED    None.
	
	Phoebe 28.8 Data/Fax     \Q3\N3\J0%C0     CONFIRMED    None.
	
	Practical Peripheral     &K3              CONFIRMED    Error Control
	14.4 FXMT                                              off. Header
	                                                      Compression off.
	                                                      Enable Software
	                                                      Compression off.
	
	Practical Peripheral     AT&F1            CONFIRMED    Remove modem and
	28.8 FXMT, SA & HCII                                   then install as a
	                                                      Standard 28.8.
	
	Practical Peripheral     None             CONFIRMED    Error Control
	28.8 LCD/PC External                                   off. Set Flow
	                                                      Control to None.
	
	Practical Peripheral     AT&F1            CONFIRMED    None.
	PC 28.8 T2-EZ
	
	Practical Peripheral     s11=50           CONFIRMED    Allow Windows 95
	PM288MCll v.34 28.8                                    to detect as a
	External                                               Standard 28.8.
	
	Practical Peripheral     AT&F1            CONFIRMED    Error Control off.
	PM28.8 HC
	
	Practical Peripheral     Unknown          UNCONFIRMED  To correct slow
	28.8 LCD/PC External                                   data transfer, set
	                                                      Error Control off,
	                                                      Flow Control to
	                                                      None, and reduce
	                                                      read ahead
	                                                      buffering on the
	                                                      Hard Disk to 4 Kb.
	
	Prometheus 14.4 Data/Fax &Q6&K3           CONFIRMED    None.
	
	Prometheus 14.4 Data/Fax \N0&K4           CONFIRMED    None.
	SoftModem
	
	Prometheus 28.8          AT&F0s11=50      CONFIRMED    For undetermined
	Cyberphone                                             reasons, the
	                                                      Prometheus
	                                                      Cyberphone series
	                                                      modems are not
	                                                      always installed
	                                                      properly by Plug
	                                                      and Play. It may
	                                                      be necessary to
	                                                      install the modem
	                                                      with the utility
	                                                      that is shipped
	                                                      with the modem to
	                                                      force it to use a
	                                                      driver not found
	                                                      in Windows 95.
	
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
