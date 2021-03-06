---
layout: page
title: "Q169903: SNA Server 3.0 Print Sessions Remain Pending on Windows NT"
permalink: /kb/169/Q169903/
---

## Q169903: SNA Server 3.0 Print Sessions Remain Pending on Windows NT

{% raw %}

	Article: Q169903
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:3.0,3.0 SP1; winnt:4.0
	Operating System(s): 
	Keyword(s): kbnetworkkbbuglist
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 3.0, 3.0 SP1 
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you run SNA Server 3.0 on Windows NT Server 4.0, an SNA Server Print
	Service session fails to start and remains in a pending status.
	
	From Sprtint.atf:
	
	  Calling EnumFontFamilies for Courier New
	  Leave, hFont=00000000
	  Leave, fGood=0
	  ERROR FontSwitch, rc=0x0
	  Leave, return_pointer=0x0, rc=1
	  SNAP-3270   S3PPPCTL  FAILED TO START JOB
	  Enter, id=0x16BFF0
	  Enter, id=0x16BFF0
	  Leave, pPrt=0016BFF0
	  Terminate job 16C004 on printer 16BFF0
	
	CAUSE
	=====
	
	The EnumFontFamilies call occasionally returns no fonts when it should return
	some, causing the print session to fail to start. This problem occurs when SNA
	Server Print Service uses EnumFontFamilies() instead of EnumFontFamiliesEx() on
	a Windows NT Server 4.0 computer.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in SNA Server 3.0 and 3.0 Service
	Pack 1 (SP1). This problem was corrected in the latest SNA Server version 3.0
	U.S. Service Pack. For information on obtaining this Service Pack, query on the
	following word in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	
	MORE INFORMATION
	================
	
	With the fix applied, the new version of enumfontfamilies(), called
	EnumFontFamiliesEx(), is used.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbnetwork kbbuglist
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbAudDeveloper kbSNAServSearch kbSNAServ300 kbSNAServ300SP1
	Version           : WINDOWS:3.0,3.0 SP1; winnt:4.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
