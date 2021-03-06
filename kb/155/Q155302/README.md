---
layout: page
title: "Q155302: XCON: Event Error 3120: A Resource Limit has Been Reached"
permalink: /kb/155/Q155302/
---

## Q155302: XCON: Event Error 3120: A Resource Limit has Been Reached

{% raw %}

	Article: Q155302
	Product(s): Microsoft Exchange
	Version(s): winnt:4.0,5.0
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 03-APR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 4.0, 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The Microsoft Exchange Message Transfer Agent (MTA) terminates with an Event ID
	9405 and the following sequence of events appears in the Event Log:
	
	  Event ID 2037 An internal MTA error occurred. There is a negative connection
	  count for locality 52. [BASE KERNEL 6 117] (10)
	
	  Event ID 2197 An MTA database server error was encountered while locking a
	  queue. Called from XAPI. Procedure 131. Database error code: ODXOINIU -
	  Object does not exist. Queue: 00000000. [DB Server TRANSFER 28 84] (14)
	
	  Event ID 2191 An MTA database server error was encountered while adding an
	  entry to a queue. Called from XAPI. Procedure 131. Database error code:
	  ODXOINIU - Object does not exist. Queue name: 00000000. Object at fault:
	  060000EE. [DB Server TRANSFER 28 62] (14)
	
	  Event ID 2198 An MTA database server error was encountered while unlocking a
	  queue. Called from XAPI. Procedure 131. Database error code: ODXOINIU -
	  Object does not exist. Queue: 00000000. [DB Server TRANSFER 28 127] (14)
	
	  Event ID 3128 An MTA database server error was encountered. [XAPI TRANSFER 28
	  131] (14)
	
	  Event ID 3120 A resource limit has been reached when attempting to open an
	  association. Number of sessions configured: 80. [XAPI MAIN BASE 1 91] (14)
	
	  Event ID 9405 An unexpected error has occurred which may cause the MTA to
	  terminate. Error: ExchHeapFree Failure. [BASE INCOMING RPC 193] (16)
	
	  Event ID 9405 An unexpected error has occurred which may cause the MTA to
	  terminate. Error: Exception e0020002 occurred at Address 77f3cbcd [BASE
	  INCOMING RPC 193] (16)
	
	Note that in the example above, these events appear in the order in which they
	occurred; they appear in this order if the Event Viewer is configured to view
	the oldest events first.
	
	CAUSE
	=====
	
	The MTA terminated due to a resource shortage. The MTA is attempting to add
	local resources for remotely-hosted connectors such as the Internet Mail
	Connector (IMC) or the MS Mail Connector (MSMI).
	
	WORKAROUND
	==========
	
	Change the following registry entry to 0x20 to avoid this resource shortage:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services
	                    \MSExchangeMTA\Parameters\MT gateway clients
	
	The default setting is 0x08 and is adequate under normal conditions. However,
	when an installation has several gateways and connectors configured, additional
	resources may be required.
	
	Additional query words: Crash SP2 stop ECB ASB shortage bind
	
	======================================================================
	Keywords          : kbusage 
	Technology        : kbExchangeSearch kbExchange500 kbExchange400 kbZNotKeyword2
	Version           : winnt:4.0,5.0
	
	=============================================================================
	

{% endraw %}
