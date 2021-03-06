---
layout: page
title: "Q238471: XIMS: How to Force SMTP Messages Through the Information Store"
permalink: /kb/238/Q238471/
---

## Q238471: XIMS: How to Force SMTP Messages Through the Information Store

{% raw %}

	Article: Q238471
	Product(s): Microsoft Exchange
	Version(s): winnt:5.0,5.5
	Operating System(s): 
	Keyword(s): exc5 exc55
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 5.0, 5.5 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SUMMARY
	=======
	
	This article explains how to reroute messages through the Microsoft Exchange
	Server information store before sending to the Internet. Enabling the rerouting
	adds some advantage because the rerouted messages have more readable addresses.
	These messages are re-routed through the information store by using the Registry
	Editor (Regedt32.exe) to set the following registry value to 1:
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSExchangeIMC\Parameters
	
	  Value Name: RerouteViaStore
	  Data Type: Reg_Dword
	  Data: 1
	
	MORE INFORMATION
	================
	
	When this registry value is set to 1, it internally enables two parameters
	required for this option to work, if they aren't already enabled, namely the
	P2Resolve and AddressRewrite parameters.
	
	If you enable rerouting of the Internet Mail Service object, then outbound
	messages are rerouted through the information store instead of being re-sent or
	"bounced" as normal. The Rerouting tab is located on the Internet Mail Server
	Routing property page, in the Configuration container.
	
	Enabling rerouting adds some advantage because the rerouted message's P1 and P2
	From field, and P2 recipients are replaced with any locally matched custom
	recipient's reply address. Addresses without matching custom recipients are not
	altered. P1 recipients continue to be rewritten in accordance with the routing
	table.
	
	Additional query words:
	
	======================================================================
	Keywords          : exc5 exc55 
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbZNotKeyword2
	Version           : winnt:5.0,5.5
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
