---
layout: page
title: "Q280449: XCON: MTA Generates 9318 Events on Multihomed Servers"
permalink: /kb/280/Q280449/
---

## Q280449: XCON: MTA Generates 9318 Events on Multihomed Servers

{% raw %}

	Article: Q280449
	Product(s): Microsoft Exchange
	Version(s): 5.5 SP4
	Operating System(s): 
	Keyword(s): kbExchange550preSP5fix
	Last Modified: 18-JUL-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 SP4 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	The Exchange Server message transfer agent (MTA) may generate remote procedure
	call (RPC) error messages that indicate that communications are failing with
	event ID 9318 on a multihomed server. This error message may occur after the MTA
	has been upgraded to build 2651.75 or later. The MTA, under certain similar
	conditions, may also generate event IDs 9266, 2219, 2206, 2207, and 9321.
	
	CAUSE
	=====
	
	This problem can occur if the network binding that the MTA needs to use is not
	the first binding available. The MTA may, under certain conditions, incorrectly
	attempt to use the first binding, and if the server is multihomed and the first
	binding is not the binding that the MTA needs to use, the MTA cannot establish a
	connection to other MTAs.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem that is described in this article. Only apply it to systems
	that are experiencing this specific problem. This fix may receive additional
	testing. Therefore, if you are not severely affected by this problem, Microsoft
	recommends that you wait for the next Microsoft Exchange Server version 5.5
	service pack that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, visit the following Microsoft
	Web site:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are ordinarily incurred for support calls
	may be canceled if a Microsoft Support Professional determines that a specific
	update will resolve your problem. The usual support costs will apply to
	additional support questions and issues that do not qualify for the specific
	update in question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	Component: MTA
	
	+--------------------------+
	| File name  | Version     | 
	+--------------------------+
	| Emsmta.exe | 5.5.2654.39 | 
	+--------------------------+
	
	
	
	WORKAROUND
	==========
	
	To work around this problem, change the order of the bindings to ensure that the
	binding that the MTA needs to use is the first in the list. In Microsoft Windows
	NT 4.0, you can gain access to the bindings in Control Panel, in the Network
	icon.
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in Microsoft Exchange Server
	version 5.5.
	
	MORE INFORMATION
	================
	
	This problem occurs because the MTA incorrectly uses code that is intended for
	use on cluster servers. The MTA does not use additional bindings on cluster
	servers to ensure that the MTA does not use the binding between the two
	clusters.
	
	For additional information about how to use this fix to resolve startup issues on
	multi-homed MTA boxes, click the article number below to view the article in the
	Microsoft Knowledge Base:
	
	  Q283238 XADM: Exchange Server 5.5 Post-SP4 Message Transfer Agent Fixes
	
	Additional query words: vinca
	
	======================================================================
	Keywords          : kbExchange550preSP5fix 
	Technology        : kbExchangeSearch kbZNotKeyword2 kbExchange550SP4
	Version           : :5.5 SP4
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
