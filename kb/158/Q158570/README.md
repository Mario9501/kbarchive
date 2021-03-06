---
layout: page
title: "Q158570: INFO: How to Determine When 3270 RTM Data Should be Sent"
permalink: /kb/158/Q158570/
---

## Q158570: INFO: How to Determine When 3270 RTM Data Should be Sent

{% raw %}

	Article: Q158570
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:2.0,2.1,2.11,3.0,4.0
	Operating System(s): 
	Keyword(s): kbenv
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 2.0, 2.1, 2.11, 3.0, 4.0, on platform(s):
	   - the operating system: Microsoft Windows NT 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	SNA Server supports the ability to report an user's 3270 response time data to
	NetView, using standard NetView Response Time Monitor (RTM) Network Management
	vector data messages. This article documents the configuration options that
	determine when RTM data is reported to NetView.
	
	When you configure 3270 Response Time Monitor (RTM) data in SNA Server Admin
	under Options and RTM Triggers, the option states the following:
	
	  RTM Data Sent at:
	
	  Select one or both of the following:
	
	  Counter Overflow: To cause RTM data to be sent to the host when the
	  number of host responses in a given time period overflows the size of
	  the available counter, select this check box.
	
	  End of Session: To cause RTM data to be sent to the host at the end of
	  each LU-to-LU session, select this check box.
	
	NOTE: It is recommended that you always choose the Counter Overflow method. If
	this is not chosen, RTM counters may "wrap" and may cause the reported data to
	be inaccurate.
	
	MORE INFORMATION
	================
	
	When the connection activates and the host is configured for RTM, the host sends
	NMVT major vector '8080' on the SSCP-PU session. This major vector includes
	subvector 92 (RTM Request) and optionally, subvector 94 (RTM Control). Subvector
	94 indicates how RTM should be measured, when the PU should send RTM data, and
	the boundaries for measurement.
	
	In some cases the host may send the RTM major vector and subvector 92, but not
	send subvector 94. In such instances, SNA Server uses the values defined in the
	"RTM Triggers" dialog box to determine how RTM should be handled. Any values
	indicated in the host subvector 94 will override the settings in SNA Admin.
	
	The IBM SNA [ASCII 147]Formats Guide[ASCII 148] states that RTM Data subvector 93
	is used to report RTM data. The counter overflow is the number of times that the
	maximum boundary of 65,535 is reached.
	
	Four sets of counters for RTM data are used to measure RTM. Each of these may be
	incremented 65,535 times before the counter overflows. These sets are defined as
	ranges that may be set in increments of 0.1 seconds (for example, 0-0.5;
	0.5-1.0; 1.0-1.5; 1.5-2.0). If a count would cause the maximum boundary for a
	set to overflow, and the SNA Server is configured to send RTM Data upon Counter
	Overflow, it will send an unsolicited NMVT with all the current counts, then
	initialize the sets.
	
	If the RTM data is set to be sent at the end of the session, the SNA Server will
	not forward the counts except in response to a request from the host or at the
	end of the session. In this case, you cannot tell whether a particular counter
	set has overflowed, so counts will not reflect the number of times the sets have
	been initialized.
	
	For additional information regarding SNA Server support for 3270 RTM data, please
	see the following:
	
	- SNA Server 3270 Emulator Interface Specification (included with SNA Server),
	  Section 3.2.4 (RTM Parameters) and 3.3.15 (Response Time Monitor Data)
	
	- Microsoft Knowledge Base article:
	
	  Q148312 No RTM Data Generated If 3270 Session Uses Exception Response
	
	Additional query words: snartm prodsna
	
	======================================================================
	Keywords          : kbenv 
	Technology        : kbAudDeveloper kbSNAServSearch
	Version           : WINDOWS:2.0,2.1,2.11,3.0,4.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
