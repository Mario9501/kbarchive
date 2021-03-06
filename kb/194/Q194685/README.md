---
layout: page
title: "Q194685: X400: Foreign System Ends Connection before Message Is Sent"
permalink: /kb/194/Q194685/
---

## Q194685: X400: Foreign System Ends Connection before Message Is Sent

{% raw %}

	Article: Q194685
	Product(s): Microsoft Mail For PC Networks
	Version(s): MS-DOS:3.2
	Operating System(s): 
	Keyword(s): 
	Last Modified: 20-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail Gateway to X.400, version 3.2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to send a message to a foreign system through the Microsoft
	Mail Gateway to X.400, the foreign system may end the connection before the
	message is completely transferred, and the X.400 log file may contain entries
	similar to the following:
	
	- 13:38:19 ERROR 3 (RTS): Sending message 0000120D failed
	
	- 13:38:19 ERROR 3 (RTS): Association aborted
	
	- 13:38:19 DEBUG (T4_recv): Connection 2: tp_receive() failed: 12
	
	- 13:38:19 ERROR 1 (MTSE): Error occurred in state 0
	
	CAUSE
	=====
	
	This problem occurs when the Microsoft Mail Gateway to X.400 sends invalid minor
	synchronization points to the foreign system.
	
	
	RESOLUTION
	==========
	
	A supported fix that corrects this problem is now available from Microsoft, but
	has not been fully regression-tested and should be applied only to systems
	experiencing this specific problem.
	
	To resolve this problem, contact Microsoft Product Support Services to obtain the
	fix. For a complete list of Microsoft Product Support Services phone numbers and
	information on support costs, please go to the following address on the World
	Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	The English version of this fix should have the following file attributes or
	later:
	
	  File Name      Version
	  ----------------------
	  X400gate.exe   3.2.8
	
	This hotfix has been posted to the following Internet location as X400gy2k.exe:
	
	  ftp://ftp.microsoft.com/bussys/mail/gateways-public/All-Y2K/
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Mail Gateway to X.400
	version 3.2.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbMailSearch kbMailGateSearch kbZNotKeyword3 kbMailGatex400320
	Version           : MS-DOS:3.2
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
