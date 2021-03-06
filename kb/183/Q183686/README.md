---
layout: page
title: "Q183686: XWEB: Cannot Identify Yourself When Posting Newsgroup Messages"
permalink: /kb/183/Q183686/
---

## Q183686: XWEB: Cannot Identify Yourself When Posting Newsgroup Messages

{% raw %}

	Article: Q183686
	Product(s): Microsoft Exchange
	Version(s): WINDOWS:5.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 22-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Outlook Web Access, version 5.5 
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	
	SUMMARY
	=======
	
	When you use Microsoft Outlook Web Access (OWA) to post messages to an anonymous
	newsgroup, you cannot specify your name or e-mail address. Other people who read
	messages that you post do not know who posted the message. In addition, when you
	use OWA to read anonymous newsgroup messages, the name of the person who posted
	the message does not appear.
	
	MORE INFORMATION
	================
	
	Microsoft recognizes the need for people to identify themselves when using OWA
	to post messages to anonymous newsgroups. We also recognize the need for people
	to know who posted messages that they read in anonymous newsgroups. We have
	modified OWA so you can specify your Simple Mail Transfer Protocol (SMTP)
	address when you post messages after logging on to a newsgroup anonymously. In
	addition, when you use OWA to read newsgroup messages posted by people who
	logged on anonymously, the person's name or e- mail address may appear.
	
	If you specify an SMTP address in the From box when you compose a message, OWA
	attempts to determine if the address is valid before it allows you to post the
	message. If it determines that the address is valid, the address is saved and
	automatically appears in the From box the next time you compose a new message.
	You can leave this default address in the From box or type a different address.
	If you type a different address and OWA determines that the address is valid,
	this new address is saved as the default address.
	
	This feature is included in the latest Microsoft Exchange Server version 5.5 U.S.
	Service Pack. For information about obtaining the Service Pack, query on the
	following word in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	
	======================================================================
	Keywords          :  
	Technology        : kbOutlookSearch kbOWASearch kbOWA550
	Version           : WINDOWS:5.5
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
