---
layout: page
title: "Q159181: XCON: Duplicate Messages Received by MS Mail Recipients"
permalink: /kb/159/Q159181/
---

## Q159181: XCON: Duplicate Messages Received by MS Mail Recipients

{% raw %}

	Article: Q159181
	Product(s): Microsoft Exchange
	Version(s): winnt:4.0,5.0,5.5
	Operating System(s): 
	Keyword(s): exc4 exc5 exc55
	Last Modified: 19-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 5.5, 4.0, 5.0 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	Messages sent to Microsoft Mail recipients through the Microsoft Exchange
	Internet Mail Connector (IMC) can result in duplicate messages. The sent and
	recv logs show the message is received and delivered multiple times. The number
	of duplicate copies received by an individual is equal to the number of
	Microsoft Mail recipients that are on the recipient list.
	
	CAUSE
	=====
	
	Any message received by the Exchange IMC has a responsibility flag set. However,
	the Windows NT, OS/2, and MS-DOS Multitasking Message Transfer Agent (MMTA)
	products do not understand the responsibility flag, and External delivers the
	message to each Microsoft Mail recipient that it finds.
	
	WORKAROUND
	==========
	
	To work around this problem:
	
	- If the originating system is a Sendmail V8 or IDA Sendmail, set the mail
	  delivery flag to allow a single message for multiple recipients.
	
	  -or-
	
	- Use of the Microsoft MSMI should also eliminate duplicate messages but this
	  requires replacing existing instances of external with MSMI connectors.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in External.exe version 3.5. A
	supported fix is now available, but has not been fully regression-tested and
	should be applied only to systems experiencing this specific problem. Unless you
	are severely impacted by this specific problem, Microsoft recommends that you
	wait for the next Service Pack that contains this fix. Contact Microsoft
	Technical Support for more information.
	
	
	MORE INFORMATION
	================
	
	For more information, see the Sendmail book published by O'Reilly and
	Associates.
	
	Additional query words: mailer
	
	======================================================================
	Keywords          : exc4 exc5 exc55 
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbExchange400 kbZNotKeyword2
	Version           : winnt:4.0,5.0,5.5
	
	=============================================================================
	

{% endraw %}
