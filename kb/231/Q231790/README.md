---
layout: page
title: "Q231790: File Sharing Operations to a Share on Local Computer May Be Slow"
permalink: /kb/231/Q231790/
---

## Q231790: File Sharing Operations to a Share on Local Computer May Be Slow

{% raw %}

	Article: Q231790
	Product(s): Microsoft Windows NT
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kbWinNT4sp6fix
	Last Modified: 16-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you share files on a computer, and then connect to that sharepoint from the
	same computer, file operations such as XCOPY may be slow if TCP/IP is the
	protocol being used.
	
	CAUSE
	=====
	
	If for example you share out a directory named "test", and then connect to that
	share from the same computer it was shared from, the TCP/IP stack uses what is
	called the "loopback" interface. The use of the "loopback" interface is to
	prevent packets between the client and server (which are on the same computer)
	from actually being sent out on the network cable.
	
	TCP/IP implements "nagling" and "delayed acknowledgment", even though the
	interface in this case is loopback. This can cause unnecessary delays.
	
	More details on nagling are available in
	ftp://ftp.microsoft.com/bussys/winnt/winnt-docs/papers/Tcpimp2.exe
	
	RESOLUTION
	==========
	
	Windows NT Server or Workstation 4.0
	------------------------------------
	
	To resolve this problem, obtain the latest service pack for Windows NT 4.0 or the
	individual software update. For information on obtaining the latest service
	pack, please go to:
	
	- http://www.microsoft.com/Windows/ServicePacks/
	
	-or-
	
	- Q152734 How to Obtain the Latest Windows NT 4.0 Service Pack
	
	For information on obtaining the individual software update, contact Microsoft
	Product Support Services. For a complete list of Microsoft Product Support
	Services phone numbers and information on support costs, please go to the
	following address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	
	Windows NT Server 4.0, Terminal Server Edition
	----------------------------------------------
	
	To resolve this problem, obtain the latest service pack for Windows NT Server
	4.0, Terminal Server Edition. For additional information, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q152734 How to Obtain the Latest Windows NT 4.0 Service Pack
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article. This problem was first corrected in
	Windows NT Server version 4.0, Terminal Server Edition Service Pack 6.
	
	Additional query words: 4.00
	
	======================================================================
	Keywords          : kbWinNT4sp6fix 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbNTTermServ400 kbNTTermServSearch
	Version           : :4.0
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
