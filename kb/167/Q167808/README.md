---
layout: page
title: "Q167808: SMS: Unable to Install or Verify NetWare Logon Servers"
permalink: /kb/167/Q167808/
---

## Q167808: SMS: Unable to Install or Verify NetWare Logon Servers

{% raw %}

	Article: Q167808
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:1.0,1.1,1.2
	Operating System(s): 
	Keyword(s): kbnetwork kbtshoot kbConfig kbSCMan smsgeneral smsconfig smssiteconfigman kbArtTypeINF
	Last Modified: 31-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 1.0, 1.1, 1.2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	NetWare logon servers in a Systems Management Server site may go inactive or
	fail to be installed, even though the Systems Management Server service account
	has adequate permissions, there is plenty of free space on the specified NetWare
	volume, and network connectivity is available. This will result in inventory
	from clients not being reported up to the site server, packages not being
	distributed, and other problems normally associated with account permissions,
	disk space, or connectivity problems.
	
	CAUSE
	=====
	
	The Site Server's Site Configuration Manager (SCMAN) may not be able to
	correctly enumerate the volume name specified in order to verify or install the
	Systems Management Server logon server components. This occurs because of a
	problem with the NetWare 3.1x logon server's bindery.
	
	Viewing the Scman.log file from the Site Server reveals that it is able to locate
	and identify the server, but is unable to enumerate the volume name specified
	for Systems Management Server installation or verification.
	
	In the following log excerpt, the number of shares (volumes) reported is
	incorrect (note that the number reported may also be 0):
	
	  Server SERVER1 has 171 shares
	  Server SERVER1 status Pending Install role 0x12
	  Server SERVER1 has 11 inboxes; 0 domain master inboxes; 0 components
	
	Site Configuration Manager attempts to identify the volume (VOL1) specified in
	the site properties, but is unable to locate it, as reflected in this portion of
	the Scman.log file:
	
	  Checking for share SMS and directory \\SERVER1\VOL1\SMS\logon.srv on SERVER1;
	  no share
	
	Directory creation is attempted, but it fails:
	
	     CSharedDirInstallItem::Install share=, vol=, dir=SMS\logon.srv,
	     subDiraccess=3, share access=2
	     Created directory \\SERVER1\VOL1\SMS\logon.srv
	     share not found, cannot create without share path
	
	An event 223 is logged:
	
	     Event 223 logged with error 183 and object (SERVER1); GetLastError 183;
	     SiteConfig Mgr code 7404.
	     Cannot create inboxes (Application Control Database, Application Control
	     INI, Application Control Script, Client Installation, Despooler,
	     Inventory Agent, Inventory Processor, ISV MIF Collection, MS Test,
	     Package Command Instruction, Package Source) on server SERVER1
	
	The logon server remains inactive.
	
	Another way to test for this condition is to browse the volume list of a NetWare
	3.1x server from an computer running Windows NT Server (for example, the site
	server) running Gateway (Client) Services for NetWare. If the volume requested
	by Site Configuration Manager is not visible in the browse list, SCMAN will not
	be able to create the directories on the volume, even though it has adequate
	permissions and connectivity and the volume has enough free space. Note that
	client computers running MS-DOS, Windows 3.x, or Windows 95 do not experience
	this problem.
	
	WORKAROUND
	==========
	
	To correct this problem, run the NetWare server BINDFIX utility for NetWare
	3.1x, and DSREPAIR for NetWare 4.x. Resetting the bindery context may also be
	helpful. For more information on these utilities, consult the documentation
	provided with your Novell NetWare product.
	
	MORE INFORMATION
	================
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q126618 Cannot See All NetWare Volumes from Windows NT
	
	
	Additional query words: prodsms enumeration
	
	======================================================================
	Keywords          : kbnetwork kbtshoot kbConfig kbSCMan smsgeneral smsconfig smssiteconfigman kbArtTypeINF 
	Technology        : kbSMSSearch kbSMS100 kbSMS110 kbSMS120
	Version           : winnt:1.0,1.1,1.2
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
