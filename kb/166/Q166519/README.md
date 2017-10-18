---
layout: page
title: "Q166519: XCON: IMS Encapsulates the X.400 O/R Address"
permalink: kb/166/Q166519/
---

## Q166519: XCON: IMS Encapsulates the X.400 O/R Address

	Article: Q166519
	Product(s): Microsoft Exchange
	Version(s): 5.0
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 30-APR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.0 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you send a message from a Defense Messaging System (DMS) client to an SMTP
	address, the message may not be successfully processed. The message gets stuck
	in the outbound Internet Mail Service (IMS) queue for the message transfer agent
	(MTA) on the server.
	
	An error message resembling the following may be generated by the IMS in the
	Application Event Log:
	
	  MSExchangeIMS
	  Event ID: 4122
	  An error occurred while retrieving the originating address of a message
	  to be delivered.
	
	  Since the originating address is needed for mail delivery, the mail
	  cannot be delivered. The message that was being processed has been moved
	  to the "BAD" folder. Use the appropriate utilities found in the SUPPORT
	  directory of your Exchange CD to view and manipulate these messages.
	
	When you attempt to view the message within the MTA queue for the IMS, the MTA
	service may stop with an error message resembling the following in the
	Application Event Log:
	
	  MSExchangeMTA
	  Event ID: 2051
	  A fatal internal MTA error occurred. Contact Microsoft Product Support
	  Services. An illegal GET from element BCC62C01 occurred at offset 12359.
	  [BASE SUBMIT 16 67] (16)
	
	CAUSE
	=====
	
	If the X.400 O/R address of the originator contains an X.500 distinguished name
	(DN) in the domain-defined attribute (DDA) field, the IMS encapsulates the X.400
	O/R address instead of using the SMTP proxy, resulting in the stated behavior.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 5.0.
	
	This problem was corrected in the latest Microsoft Exchange Server 5.0 U.S.
	Service Pack. For information on obtaining the service pack, query on the
	following word in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	
	======================================================================
	Keywords          : kbusage 
	Technology        : kbExchangeSearch kbExchange500 kbZNotKeyword2
	Version           : 5.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	