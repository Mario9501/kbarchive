---
layout: page
title: "Q200730: SMS: NetWare Clients Do Not Show NetBIOS Machine Name"
permalink: /kb/200/Q200730/
---

## Q200730: SMS: NetWare Clients Do Not Show NetBIOS Machine Name

{% raw %}

	Article: Q200730
	Product(s): Microsoft Systems Management Server
	Version(s): 1.2,1.2 SP1,1.2 SP2,1.2 SP3,1.2 SP4
	Operating System(s): 
	Keyword(s): kbnetwork kbsetup kbsms200 kbsms120 kbsms120bug kbsmsAdmin smsadmin smssetup
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 1.2, 1.2 SP1, 1.2 SP2, 1.2 SP3, 1.2 SP4 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Novell NetWare uses IPX as the default network protocol. NetWare does not use
	NetBIOS machine names for client identification purposes; NetWare uses the ID of
	the user who is logged on and the computer (MAC) address of the Network
	Information Center instead. Consequently, it is possible to have duplicate
	machine names on the network in a NetWare environment. Therefore, when a NetWare
	client computer becomes a Systems Management Server client, the ID data that is
	used is indeed the MAC address.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem that is described in this article. Only apply it to systems
	that are experiencing this specific problem. This fix may receive additional
	testing. Therefore, if you are not severely affected by this problem, Microsoft
	recommends that you wait for the next Systems Management Server version 1.2
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
	
	  Date         Time         Size     File name    Platform
	  ---------------------------------------------------------
	  06/07/2001   03:45 P.M.   8,1012   Invdos.exe   Intel
	
	NOTE: Because of file dependencies, the most recent fix or feature that contains
	the above files may also contain additional files.
	
	
	WORKAROUND
	==========
	
	To work around this problem and have the computers report their NetBIOS machine
	names to the Systems Management Server administrator console, use one of the
	following methods:
	
	- Have the clients log on to Microsoft Windows NT, or LAN Manager Domain
	  controller by using a NetBIOS-compatible transport such as TCP/IP or NetBEUI.
	
	- For Microsoft Windows 3.1, Microsoft Windows for Workgroups 3.11, Microsoft
	  Windows 95, or Microsoft Windows 98 clients, use the /M switch for Invdos.exe
	  to specify the client's machine identifier (machine name). If the fix that
	  this article describes is not applied, the user must manually enter the
	  machine name at the time that Invdos.exe is run (during logon) to use the /M
	  switch. The fix that this article describes updates the /M switch
	  functionality to optionally allow a user to specify a machine identifier on
	  the command line for Invdos.exe. To specify a machine name on the command
	  line, append the machine name that you want to use to the /M switch when you
	  call Invdos.exe. This allows you to use an environment variable that contains
	  a machine-specific identifier to override the default SMS identifier
	  convention (MAC address).
	
	  NOTE: When you use this method to override the default naming convention, make
	  sure that each computer receives a unique identifier to prevent duplication
	  in the SMS database.
	
	  The following command line is the correct usage:
	
	  INVDOS /M<machine_name>
	
	  NOTE: Do not include a space between the /M switch and the machine name that
	  you want to use.
	
	  The following code is sample usage in SMSLS script that identifies the client
	  with the value in the environment variable "MACHINENAME" on that client:
	
	  setls%SMS_OS% -m:E -i -p:%SMS_BIN%\INVDOS.EXE -pa:/m%MACHINENAME% -pa:/l:%%SMS_UNC%%\ -pa:/i -pa:%SMS_VERBOSE%
	
	  NOTE: The use of the /pa: switch is required for the Setls.exe command line to
	  indicate to Setls that the data that follows is an argument for Invdos.exe,
	  and not for Setls itself. For additional information about the Setls.exe or
	  Invdos.exe command-line options, see chapter 2 of the SMS Resource Guide.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	version 1.2.
	
	MORE INFORMATION
	================
	
	The fix that this article describes updates the /M switch functionality to allow
	a machine identifier to be specified optionally on the command line for
	Invdos.exe
	
	Additional query words: prodsms NIC
	
	======================================================================
	Keywords          : kbnetwork kbsetup kbsms200 kbsms120 kbsms120bug kbsmsAdmin smsadmin smssetup 
	Technology        : kbSMSSearch kbSMS120 kbSMS120SP2 kbSMS120SP3 kbSMS120SP4 kbSMS120SP1
	Version           : :1.2,1.2 SP1,1.2 SP2,1.2 SP3,1.2 SP4
	Hardware          : x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
