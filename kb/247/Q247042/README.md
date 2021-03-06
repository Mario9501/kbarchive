---
layout: page
title: "Q247042: SNA Windows NT Client Fails on Windows 2000 Terminal Server"
permalink: /kb/247/Q247042/
---

## Q247042: SNA Windows NT Client Fails on Windows 2000 Terminal Server

{% raw %}

	Article: Q247042
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:2.11 (all versions),3.0 (all SP),4.0,4.0 SP1,4.0 SP2
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 2.11, 2.11 SP1, 2.11 SP2, 3.0 SP1, 3.0 SP2, 3.0 SP3, 3.0 SP4, 4.0, 4.0 SP1, 4.0 SP2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When the SNA Server client for Windows NT is installed on a computer running
	Windows 2000 Terminal Server, the SnaBase Service fails to start. For example,
	if the 3270 applet is started in a Terminal Server session connected to a
	Windows 2000 Server computer, the following error message occurs:
	
	  ERROR - The SnaBase Service is not started.
	
	Other SNA Server client components may simply stop responding. The Windows 95
	client does not have any problem running in the same environment.
	
	Note: This problem occurs even after the SNA Windows NT client binaries are
	registered using the Terminal Services command file that is distributed with SNA
	Server.
	
	CAUSE
	=====
	
	The SNA Server Windows NT client software components share a global-memory
	mapped file region on the computer, and use named events for the SnaBase service
	and SNA applications to coordinate operations with each other. However, SNA
	applications are unable to locate the shared memory segment created by the
	SnaBase service when they are run under Windows 2000 Terminal Services (WTS).
	This is because WTS requires that these applications prepend any named memory
	and named events with a "Global\" name prefix.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for SNA Server 4.0. For
	additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q215838 How to Obtain the Latest SNA Server Version 4.0 Service Pack
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article. This problem was first corrected in SNA
	Server 4.0 Service Pack 3.
	
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ211 kbSNAServ400 kbSNAServ211SP1 kbSNAServ211SP2 kbSNAServ300SP3 kbSNAServ300SP1 kbSNAServ400SP1 kbSNAServ400SP2 kbSNAServ300SP2 kbSNAServ300SP4
	Version           : WINDOWS:2.11 (all versions),3.0 (all SP),4.0,4.0 SP1,4.0 SP2
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
