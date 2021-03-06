---
layout: page
title: "Q221522: XCLN: Adding Address from GAL to PAB in Outlook 97 May Not Work"
permalink: /kb/221/Q221522/
---

## Q221522: XCLN: Adding Address from GAL to PAB in Outlook 97 May Not Work

{% raw %}

	Article: Q221522
	Product(s): Microsoft Exchange
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 22-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Outlook 97 
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	You can select multiple addresses from the global address list and add them to
	the Personal Address Book (PAB). However, in some situations, you may receive
	the following error message:
	
	  Some names could not be added to the Personal Address Book. One or more of
	  the selected entries could not be copied.
	
	Also, none of the selected addresses are added to the PAB.
	
	CAUSE
	=====
	
	You receive this error message when you select multiple addresses to add to the
	PAB and one of these addresses is the Microsoft Schedule+ Free/Busy Connector
	(alias: ADMINSCH). This address is not a regular user mailbox and does not have
	a corresponding Microsoft Windows NT User Account associated with it. It is used
	internally by Microsoft Exchange Server for exchanging free and busy information
	with other sites.
	
	WORKAROUND
	==========
	
	Ensure that the Microsoft Schedule+ Free/Busy Connector is not on the list of
	addresses that you are adding to the PAB.
	
	MORE INFORMATION
	================
	
	The Microsoft Schedule+ Free/Busy Connector is classified as a mailbox agent. A
	mailbox agent sends and receives messages and provides mailbox routing and
	schedule information to the message transfer agent (MTA) and connectors. Users
	do not need to send a message to the Microsoft Schedule+ Free/Busy Connector. It
	is advisable to hide this address from the global address list so that users
	cannot send mail to it. For additional information on how to do this, click the
	article number below to view the article in the Microsoft Knowledge Base:
	
	  Q177768 XADM: How to Hide the Schedule+ Free/Busy Connector
	
	Differences for Outlook 98 and Outlook 2000
	-------------------------------------------
	
	In Outlook 98 and Outlook 2000, when a similar operation is performed, you may
	receive the following error message :
	
	  Some names could not be added to the Personal Address Book. The action could
	  not be completed.
	
	However, all the selected addresses from the global address list, except the
	Microsoft Schedule+ Free/Busy Connector, are added to the PAB. Therefore, you
	may safely ignore the error message.
	
	Additional query words: 8.0 8.01 8.02 8.03 8.04
	
	======================================================================
	Keywords          :  
	Technology        : kbOutlookSearch kbOutlook97Search kbZNotKeyword3
	Version           : :
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
