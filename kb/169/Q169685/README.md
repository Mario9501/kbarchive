---
layout: page
title: "Q169685: XFOR: When Remote Clients Support MAPI, BP9 not Sent"
permalink: /kb/169/Q169685/
---

## Q169685: XFOR: When Remote Clients Support MAPI, BP9 not Sent

{% raw %}

	Article: Q169685
	Product(s): Microsoft Exchange
	Version(s): WinNT:5.0
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 12-MAY-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.0 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	Forwarding messages by way of an X.400 connector may result in messages without
	a message body part arriving at foreign (non-Exchange) X.400 systems. This
	represents a loss of data in these foreign systems.
	
	CAUSE
	=====
	
	When you select the "Remote clients support MAPI" check box on the X.400
	Connector general property page, this causes the Microsoft Exchange message
	transfer agent (MTA) to drop the X.400 protocol for forwarded messages. As a
	result, non-Exchange systems may see messages that do not have a message body
	part.
	
	WORKAROUND
	==========
	
	To work around this problem:
	
	- Do not select the "Remote clients support MAPI" check box on the X.400
	  Connector general property page.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 5.0. This problem has been corrected in the latest U.S. Service Pack for
	Microsoft Exchange Server version 5.0. For information on obtaining the service
	pack, query on the following word in the Microsoft Knowledge Base (without the
	spaces):
	
	  S E R V P A C K
	
	
	MORE INFORMATION
	================
	
	Even though the Microsoft Exchange MTA behaves as it has been configured,
	Microsoft recognizes the need to be able to send the X.400 protocol along with
	the message.
	
	The need for the required behavior discussed in this article should become more
	distinct by looking at the scenario outlined below.
	
	Microsoft Exchange Server acts as a common backbone for both Microsoft Exchange
	Server systems and non-Exchange X.400 systems. At Exchange systems off the
	backbone, administrative burden can be eased, by using a minimal configuration
	to connect to the Exchange X.400 backbone. This minimal configuration could for
	example include an address space of 'C=*' on the X.400 connector to the
	backbone. On the same connector, the 'Remote clients support MAPI' check box is
	activated, for maximal Exchange interoperability.
	
	Without the hotfix discussed here, the X.400 protocol for forwarded messages
	would be dropped for messages sent over such an X.400 connector. On forwarding
	such a message from the Exchange backbone to a non-Exchange system, data loss
	will occur, because the message will not have a message body part.
	
	The X.400 protocol for forwarded messages is sometimes referred to as BP9. Please
	note that the MS Exchange MTA behaves as described in this article, because it
	is configured that way. The fix discussed herein allows to configure the wanted
	behavior on a per connector basis. The default behavior for Exchange is to drop
	BP9 on X.400 links configured with the option 'Remote clients support MAPI'.
	Please do the following to allow BP9 being sent additionally, after applying the
	hotfix, for EACH X.400 connector you want Exchange's default setting to be
	changed:
	
	1. Start the Exchange Admin module in raw mode using the following syntax:
	
	  ADMIN -R
	
	2. Change to the Connections container.
	
	3. Highlight the X.400 connector that you want to change.
	
	4. Click the Raw Properties entry on the File menu. This brings up the
	  raw-property page of the selected connector.
	
	5. In the "List attributes of type" box in the lower left corner of the property
	  page, select "Non existing".
	
	6. In the "Object attributes" list, select the Heuristics property by clicking
	  it.
	
	7. In the "Edit value" field enter 512 (0x200 hex) and click the Set button. It
	  should become active when you type the value.
	
	8. Click Apply and then click OK. This should close the raw-property page for
	  this connector.
	
	9. Check that your modifications have been applied properly by opening the
	  raw-property page of the modified connector again. The "Heuristics" property
	  with a value of 512 should show up, after "Existing" objects in the "List
	  attributes of type" select box have been chosen.
	
	10. Repeat steps 1 through 9 for each connector you want to modify.
	
	11. If you want the modifications to take effect immediately, stop and restart
	  the service Microsoft Exchange message transfer agent.
	
	
	INSTALLATION
	
	1. Run HOTFIX /I at a Windows NT command prompt.
	
	2. Run HOTFIX /V at a Windows NT command prompt to verify that the fixed files
	  have been installed properly.
	
	3. Before proceeding to step 4, refer to the configuring instructions in the
	  "More Information" section of this article.
	
	4. For your changes to take effect, you must stop and restart all Microsoft
	  Exchange Server services.
	
	======================================================================
	Keywords          : kbusage 
	Technology        : kbExchangeSearch kbExchange500 kbZNotKeyword2
	Version           : WinNT:5.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
