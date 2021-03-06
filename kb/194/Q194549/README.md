---
layout: page
title: "Q194549: X400: Message Sent to Invalid Recipient Generates Second NDR"
permalink: /kb/194/Q194549/
---

## Q194549: X400: Message Sent to Invalid Recipient Generates Second NDR

{% raw %}

	Article: Q194549
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
	
	When you attempt to send a message to a single X.400 recipient, and the
	Microsoft Mail Gateway to X.400 is unable to deliver the message, you may
	receive a non-delivery report (NDR) that is not associated with the original
	message, and the following entry may appear in the System.log file:
	
	  [024] Message was not delivered: routing file was corrupted.
	
	CAUSE
	=====
	
	When the Microsoft Mail Gateway to X.400 is unable to deliver a message, the
	gateway creates a non-delivery report (NDR) and an associated P1 file. If the
	message was sent to a single recipient, the NDR and P1 file are created with no
	recipients. Even though the NDR does not contain any valid recipients, the
	gateway may attempt to send the NDR. When the External program attempts to
	deliver the NDR, an additional NDR is generated, and the above entry is added to
	the System.log file.
	
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
