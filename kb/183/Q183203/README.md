---
layout: page
title: "Q183203: Print Queue Backs Up When Connected to NetWare Server via LPR"
permalink: /kb/183/Q183203/
---

## Q183203: Print Queue Backs Up When Connected to NetWare Server via LPR

{% raw %}

	Article: Q183203
	Product(s): Microsoft Windows NT
	Version(s): WinNT:3.51,4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 10-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Your Windows NT Print Server may back up or not complete print jobs when it is
	configured to send print jobs to a Novell NetWare Server through line printer
	remote (LPR).
	
	CAUSE
	=====
	
	The Novell NetWare server may be resetting the Transmission Control Protocol
	(TCP) ports.
	
	RESOLUTION
	==========
	
	To resolve this issue you will need to contact Novell technical support.
	
	For information about how to contact Novell, query in the Knowledge Base for one
	of the following articles:
	
	  ARTICLE-ID: Q65416
	  TITLE : Hardware and Software Third-Party Vendor Contact List, A-K
	
	  ARTICLE-ID: Q60781
	  TITLE : Hardware and Software Third-Party Vendor Contact List, L-P
	
	  ARTICLE-ID: Q60782
	  TITLE : Hardware and Software Third-Party Vendor Contact List, Q-Z
	
	
	STATUS
	======
	
	Novell NetWare is manufactured by Novell, a vendor independent of Microsoft; we
	make no warranty, implied or otherwise, regarding this products' performance or
	reliability.
	
	MORE INFORMATION
	================
	
	In high volume print environments, more then ten print jobs may queue up in the
	print spooler at the same time. Per RFC 1179, each one of these jobs opens a TCP
	session with the receiving line printer daemon (LPD) server. Although multiple
	sessions are expected behavior, when the Novell NetWare server sees that more
	than ten sessions are trying to setup from the same source address it
	incorrectly thinks it is under a SYN attack. To defend itself from this, it
	resets all connections from the source IP address.
	
	Additional query words: printing hang hanging stop stick
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNT351search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS351search
	Version           : WinNT:3.51,4.0
	Hardware          : ALPHA x86
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
