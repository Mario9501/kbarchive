---
layout: page
title: "Q171790: Time Incorrect After Restarting Multiprocessor System"
permalink: /kb/171/Q171790/
---

## Q171790: Time Incorrect After Restarting Multiprocessor System

{% raw %}

	Article: Q171790
	Product(s): Microsoft Windows NT
	Version(s): WinNT:3.51,4.00
	Operating System(s): 
	Keyword(s): kbenv kbWinNT400sp4fix
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 3.51, 4.0 
	- Microsoft Windows NT Server versions 3.51, 4.0 
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	On a multiprocessor computer, if you synchronize the system time to an external
	time source using the Date/Time tool in Control Panel, and then restart your
	system, the system time will be slow by four to five seconds for every processor
	after the first processor.
	
	Example:
	
	If you set the time on a 4-processor system, the system time will be 12-15
	seconds slow (3 x 4-5 seconds). Note that the time loss is not cumulative; the
	system will still be slow by the same amount after another restart unless the
	time is changed again.
	
	CAUSE
	=====
	
	During system initialization, the system starts by using only one processor. The
	system time is retrieved from the system Real Time Clock (RTC) and loaded into
	the system clock. Later in the initialization process, the system clock timer is
	halted for four to five seconds while each additional processor is configured.
	This halting causes a time slip from the RTC value. When the time is written, it
	is written to both the system clock and to the RTC.
	
	RESOLUTION
	==========
	
	To work around this problem, perform one of the following:
	
	- Synchronize the system time with an external source and restart. Determine
	  how much time the system lost during startup, and set the system time fast by
	  this amount. After a restart, the time should be correct. You will need to
	  repeat this procedure every time the system time is set.
	
	- Run the time service provided in the resource kit. This will keep a group of
	  servers in sync with each other.
	
	
	To resolve this problem, obtain the latest service pack for Windows NT 4.0 or
	Windows NT Server 4.0, Terminal Server Edition. For additional information,
	please see the following article in the Microsoft Knowledge Base:
	
	  Q152734 How to Obtain the Latest Windows NT 4.0 Service Pack
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT 4.0 and Windows NT
	Server 4.0, Terminal Server Edition. This problem was first corrected in Windows
	NT 4.0 Service Pack 4.0 and Windows NT Server 4.0, Terminal Server Edition
	Service Pack 4.
	
	
	Microsoft has confirmed this to be a problem in Windows NT version 3.51. We are
	researching this problem and will post new information here in the Microsoft
	Knowledge Base as it becomes available.
	
	======================================================================
	Keywords          : kbenv kbWinNT400sp4fix 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT351search kbWinNT400search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbNTTermServ400 kbNTTermServSearch kbWinNTS351search
	Version           : WinNT:3.51,4.00
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
