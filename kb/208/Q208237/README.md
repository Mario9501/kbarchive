---
layout: page
title: "Q208237: Troubleshooting Event ID 5711 Recorded on the PDC"
permalink: /kb/208/Q208237/
---

## Q208237: Troubleshooting Event ID 5711 Recorded on the PDC

{% raw %}

	Article: Q208237
	Product(s): Microsoft Windows NT
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kbenv kberrmsg
	Last Modified: 04-MAR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Event ID 5711 (Successful partial domain synchronization) is an informational
	event, you generally see on the PDC. This event indicates that a successful
	synchronization event has occured with a BDC.
	
	MORE INFORMATION
	================
	
	If you observe these event IDs on the PDC, it is not an issue unless
	synchronization is happening too often. There are several causes for a large
	numbers of Event ID 5711's recorded in the event log of the PDC, and this could
	indicate an issue. This article is designed to help determine the cause of the
	large number of events.
	
	1. Check to see if any built-in accounts have been modified. For example:
	
	   - The administrator for the domain has been removed from the Administrators
	     group on the domain controller.
	   - The Administrator's account is made a non-Administrator account.
	   - The Administrator's account is disabled using the "Disable account" check
	     box.
	   - The Administrator's account is configured to expire.
	   - The Domain Admins global group is removed from the Administrators local
	     group.
	   - The administrator is removed from the Domain Admins global group.
	
	  For additional information about Event ID 5711, click the article number below
	  to view the article in the Microsoft Knowledge Base:
	
	  Q161569 Event ID 5711 Fills Event Log on Primary Domain Controller
	
	2. Check for an account lockout. Account lockout can cause immediate
	  synchronization and a large number of event ID 5711 messages. You can detect
	  account lockouts using the following tools:
	
	   - Checked version of Netlogon.dll
	   - Event Viewer
	   - Network Monitor
	   - User Manager for Domains
	
	  For additional information about account lockouts, click the article number
	  below to view the article in the Microsoft Knowledge Base:
	
	  Q191828 Account Lockouts and 5711 Events on the PDC
	
	3. Install the checked version of Netlogon.dll. If you use the correct debug
	  flag configuration (0x29b6ffff), you can observe what gets written to the
	  Changelog file. You can use the log file to help determine the cause of the
	  large number of 5711 events.
	  For additional information about account lockouts, click the article number
	  below to view the article in the Microsoft Knowledge Base:
	
	  Q189541 Using the Checked Netlogon.dll to Track Account Lockouts
	
	4. You can also install the debug version of Netlogon and run some tests to
	  balance processor utilization and network utilization for database
	  synchronization. Using the correct debug flag configuration (0x29b6ffff), you
	  can observe what gets written to the Changelog and measure the start and end
	  times for SAM database synchronization.
	
	  For testing purposes generate 1, 10, 50, 100, or 500 changes then measure
	  [(End time - Start time) / # of changes] to understand the number of changes
	  that can be replicated.
	
	There are a few domain tuning issues that can have an effect on the number of
	5711 events. For additional information, click the article number below to view
	the article in the Microsoft Knowledge Base:
	
	  Q238191 Partial Replication May Take a Long Time with Very Large Groups
	
	If you install the Service Pack 4 version of the Netlogon.dll file, the secure
	channels for BDCs are not dropped when there are more than 250 machine accounts.
	For additional information, click the article number below to view the article
	in the Microsoft Knowledge Base:
	
	  Q154398 BDC Secure Channel May Fail if More Than 250 Computer Accounts
	
	You can install Service Pack 4, which installs a new version of the Samsrv.dll
	file on the PDC to avoid immediate SAM syncronization for machine account
	password changes. For additional information, click the article number below to
	view the article in the Microsoft Knowledge Base:
	
	  Q154502 Replication Increased by ANNOUNCE_IMMEDIATE
	
	For additional information, click the article number below to view the article in
	the Microsoft Knowledge Base:
	
	  Q175468 Effects of Machine Account Replication on a Domain
	
	If you are running Service Pack 4, investigate disabling or increasing the
	machine account password change policy. There are three ways to resolve machine
	account replications.
	
	- Add the following registry parameter on all Windows NT workstations:
	
	  Key     = HLM\SYSTEM\CurrentControlSet\Services\NetLogon\Parameters
	  Value   = DisablePasswordChange REG_DWORD 1
	  Default = 0
	
	  NOTE: This registry key prevents you from changing passwords on workstations.
	  You could add this registry value after having joined the domain and
	  restarted the computer, so that the computer account password would have at
	  least been changed once with a random value only known by the computer.
	- Refuse passwords changed at domain controllers levels. On all domain
	  controllers, add the following registry value:
	
	  Key     = HLM\SYSTEM\CurrentControlSet\Services\NetLogon\Parameters
	  Value   = RefusePasswordChange REG_DWORD 1
	  Default = 0
	
	  For additional information, click the article number below to view the article
	  in the Microsoft Knowledge Base:
	
	  Q154501 How to Disable Automatic Machine Account Password Changes
	
	- A new parameter has been added as a hotfix in order to change the frequency
	  at which workstations change secure channel password. You can add it to all
	  workstations and also on all BDCs. (This hotfix is the Service Pack 4 version
	  of the Samsrv.dll file.)
	
	  Key     = HLM\SYSTEM\CurrentControlSet\Services\NetLogon\Parameters
	  Value   = MaximumPasswordAge REG_DWORD
	  Default = 7
	  Range   = 1 to 1,000,000 (in days)
	
	Additional query words:
	
	======================================================================
	Keywords          : kbenv kberrmsg 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : :4.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
