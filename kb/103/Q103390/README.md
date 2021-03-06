---
layout: page
title: "Q103390: Network Access Validation Algorithm and Example"
permalink: /kb/103/Q103390/
---

## Q103390: Network Access Validation Algorithm and Example

{% raw %}

	Article: Q103390
	Product(s): Microsoft Windows NT
	Version(s): 3.1 3.5 3.51 4.0
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Advanced Server, version 3.1 
	- Microsoft Windows NT Server versions 3.5, 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	The following is a simplified algorithm that explains how Windows NT
	Advanced Server account validation is observed to function during
	network access. This discussion does not cover the internal workings
	of this process. With this information, you can predict Windows NT
	network logon behavior under deterministic conditions.
	
	Keep in mind when following this article that the local database is the
	ONLY
	database on a domain controller.  But on the other server and all
	workstations the local database is different than the domain controller.
	
	NOTE: All references to Windows NT Advanced Server in this article also
	include Windows NT Server.
	
	Background Information
	----------------------
	
	When two Microsoft network systems communicate over a network, they
	use a high-level protocol called server message block (SMB). These
	commands are embedded within the transport protocols like NetBEUI or
	TCP/IP. When a client carries out a NET USE command, it sends out a
	"SMB Session Setup and X" frame.
	
	In Windows NT, the Session Setup SMB includes the user account, a
	
	  function of the encrypted password and login domain. An Advanced
	
	Server will look at all of this information to determine if the client
	has permissions to complete the NET USE command.
	
	Algorithm
	---------
	
	Windows NT workstation sends the following command to an Advanced
	Server:
	
	  NET USE x: \\server\share
	
	The Windows NT client sends a Session Setup SMB that contains its
	
	   Login Domain, User Account and Password.
	
	The Advanced Server checks the SMB specified Domain name
	If  the domain is the Advanced Server's own Domain then
	
	   It checks its own Domain SAM[Security Account Manager]database for
	       a matching account.
	   If  it finds a matching account then
	       The SMB password is compared to the Domain Database password.
	       If  the password matches then
	           The Command Completed Successfully.
	       If  the password does NOT match then
	           User is prompted for a password.
	               It is retested as above.
	           System error 1326 has occurred.  Logon failure: unknown
	           user name or bad password.
	       End
	   If  it does NOT find the account in the domain SAM database then
	       Guest permissions are tested.
	       If  the Guest account is Enabled
	           The Command Completed Successfully.
	       If  the Guest account is Disabled
	           * See Note A.
	           User is prompted for a password.
	           System error 1326 has occurred.  Logon failure:
	               unknown user name or bad password.
	       End
	
	If  the Domain specified in the SMB is one that the Advanced Server TRUSTS then
	
	   The Advanced Server will do pass through authentication.  The
	       network logon request will be sent to an Advanced Server in the
	       specified Trusted Domain.
	
	
	   The Trusted Domain Advanced Server checks its own Domain database
	       for a matching account.
	   If  it finds a matching account then
	       It looks to see if the Account is a Local or Global Account.
	       If  the Account is Local then
	           Guest permissions on the Original Server are tested.
	           If  the Guest account is Enabled
	               The Command Completed Successfully.
	           If  the Guest account is Disabled
	               * See Note A.
	               User is prompted for a password.
	               System error 1326 has occurred.  Logon failure:
	               unknown user name or bad password.
	       End
	       If  the Account is Global
	           The SMB password is compared to the Domain Database
	               password.
	           If  the password matches then
	               The Command Completed Successfully.
	               * See Note B.
	           If  the password does NOT match then
	               User is prompted for a password.
	                   It is retested as above.
	               System error 1326 has occurred.  Logon failure:
	               unknown user name or bad password.
	       End
	   If  it does NOT find the account in the Trusted domain
	           database then
	       Guest permissions are tested on the ORIGINAL Advanced
	           Server -NOT the Trusted Advanced Server.  * See Note C.
	       If  the Guest account is Enabled
	           User will have original server guest access.
	           The Command Completed Successfully.
	       If  the Guest account is Disabled
	           * See Note A.
	           User is prompted for a password.
	           System error 1326 has occurred.  Logon failure:
	               unknown user name or bad password.
	   End
	
	If  the Domain specified in the SMB is UNKNOWN by the Advanced Server. 
	[A Domain was specified but it was not recognized by the Server as a 
	Trusted Domain or its own.]
	
	   It  will check its own Domain Account Database for
	       a matching account
	   If  the Advanced Server finds a matching account then
	       The SMB password is compared to the Domain Database password.
	       If  the password matches then
	           The Command Completed Successfully.
	       If  the password does NOT match then
	           The User is prompted for a password.
	               It is retested as above.
	           System error 1326 has occurred.  Logon failure: unknown
	           user name or bad password.
	   End
	   If  it does NOT find the account in the domain database then
	       Guest permissions are tested.
	       If  the Guest account is Enabled
	           The Command Completed Successfully.
	       If  the Guest account is Disabled
	           System error 1326 has occurred.  Logon failure:
	           unknown user name or bad password.
	   End
	
	If  the Domain specified in the SMB is NULL [None specified] then
	
	   The Advanced Server will treat this a local network logon.  It
	       will check for a matching account in its own SAM Database.
	   If  it finds a matching account then
	       The SMB password is compared to the SAM Database password.
	       If  the password matches then
	           The Command Completed Successfully.
	       If  the password does NOT match then
	           The User is prompted for a password.
	               It is retested as above.
	           System error 1326 has occurred.  Logon failure: unknown
	           user name or bad password.
	   End
	   If  it does NOT find the account in the local SAM Database then
	       The Advanced Server will Simultaneously ask another Advanced
	           Server in each Domain that it Trusts if it has account that
	           matches the SMB account.
	       The first Trusted Advanced Server to reply is sent a request to
	           perform pass through authentication of the client
	           information.
	       The Trusted Advanced Server will look in its own SAM Database.
	       If  an account that matches the SMB account is found then
	           It looks to see if the Account is a Local or Global
	               Account.
	           If  the Account is Local then
	               Guest permissions on the original Server are tested.
	               If  the Guest account is Enabled
	                   The Command Completed Successfully.
	               If  the Guest account is Disabled
	               The user will be prompted for a password.
	               No matter what password is entered, user will receive
	                   "Error 5: Access has been denied."
	           End
	           If  the Account is Global
	               The password specified in the SMB is compared
	                   to the SAM Database password.
	               If  the password matches then
	                   The Command Completed Successfully.
	               If  the password does NOT match then
	                   The User is prompted for a password.
	                       It is retested as above.
	                   System error 1326 has occurred.  Logon failure:
	                   unknown user name or bad password.
	           End
	   If  no Trusted Domains respond to request to identify the
	       account then
	       Guest permissions are tested on the Original Advanced Server -
	           not the Trusted server.
	       If  the Guest account is Enabled
	           The Command Completed Successfully.
	       If  the Guest account is Disabled
	           System error 1326 has occurred.  Logon failure:
	           unknown user name or bad password.
	   End
	
	Notes
	-----
	
	1. At the point that the GUEST account is disabled and the user does not have an
	  account, the Windows NT Server will still request a password. Although no
	  password will meet its requirements, it will still request it. This is a
	  security measure. It insures that an unauthorized user cannot tell the
	  difference between a case where an account exists and when the account does
	  not exist. Password prompting always occurs regardless if the account exists.
	
	2. At this point, the following information is returned from the Trusted Domain
	  in the Response: Domain SID, User ID, Global Groups Memberships, Logon Time,
	  Logoff Time, KickOffTime, Full Name, Password LastSet, Password Can Change
	  Flag, Password Must Change Flag, User Script, Profile Path, Home Directory
	  and Bad Password Count.
	
	
	- Guest account only matters in the domain of the Server you are attempting to
	  access. Guest accounts on trusted domains never come into play.
	
	- All steps above assume Global Account unless specified as Local Account. See
	  the "Concepts and Planning Guide" for more information on account types.
	
	- The actual internal process is more complicated than the steps described
	  above.
	
	- This does not cover the actual pass-through authentication mechanics. For
	  more information, query on the following words in the Microsoft Knowledge
	  Base:
	
	  authentication and msv
	
	- This does not cover the password encryption process used in Windows NT. For
	  more information, query on the following words in the Microsoft Knowledge
	  Base:
	
	  authentication and msv
	
	  A function of the One Way Encrypted password is sent.
	
	- This article does not detail the internal workings of the MS Authentication
	  Module.
	
	- The above model assumes that the Guest Account, when enabled, has no
	  password. This is the default in Windows NT. If a guest account password is
	  specified, it must match the users password that sends in the SMB.
	
	Example
	-------
	
	The following are examples of this algorithm in action:
	
	I am logged on to my Windows NT workstation local computer. I am using
	the same account name and password that is in SCRATCH-DOMAIN Advanced
	Server Domain account database. When I carry out the NET USE \\SCRATCH
	(Domain Controller for SCRATCH-DOMAIN) command, the command completes
	successfully. When I carry out the NET USE \\NET (Controller that
	Trust SCRATCH-DOMAIN) command. I receive the error message "System
	error 1326 has occurred. Logon failure: unknown user name or bad
	password." My account \SCRATCH-DOMAIN\USER1 has permissions on \\NET?
	What is the problem?
	
	Configurations
	--------------
	
	Windows NT workstation:
	
	 -Login account: USER1
	 -Password:      PSW1
	 -Login Domain:  LOCAL1
	
	Windows NT Advanced Server:
	
	 -Server Name:            NET</ITEM>
	 -Advanced Server Domain: NET-DOMAIN</ITEM>
	 -Trust:                  NET-DOMAIN Trust SCRATCH-DOMAIN (Therefore,
	                          accounts on SCRATCH-DOMAIN can be granted permissions 
	                          in the NET- DOMAIN.
	
	- Domain Account Database for NET-DOMAIN does NOT contain an account for USER1.
	
	- Guest Account is DISABLED.
	
	Windows NT Advanced Server:
	
	 -Server Name:                       SCRATCH
	 -Advanced Server Domain:            SCRATCH-DOMAIN
	 -Domain Database contains account:  USER1
	 -Domain Database contains password: PSW1
	
	Answer
	------
	
	In this example, the Windows NT workstation is logged on to its local
	workstation domain--not the Advanced Server SCRATCH-DOMAIN where its
	domain account resides.
	
	NET USE x: \\NET\share
	
	- When the Windows NT workstation carried out the NET USE x: \\NET\share
	  command, it sent out account = "USER1", password = "PSW1" and domain =
	  "LOCAL1" in the Session Setup SMB.
	
	- The Advanced Server \\NET received the SMB and looked at the account name.
	
	- It looks in its local domain account database and does not find a match.
	
	- \\NET then looks at the SMB Domain name.
	
	- It does not trust "LOCAL1" so it does not check any of its trusted domains.
	
	- \\NET then checks its Guest account.
	
	- The guest account is disabled so the "System error 1326 has occurred. Logon
	  failure: unknown user name or bad password." message is generated.
	
	NET USE x: \\SCRATCH\share
	
	- When the Windows NT workstation carried out the NET USE x: \\SCRATCH\share
	  command, it sent out account = "USER1", password = "PSW1" and domain =
	  "LOCAL1" in the Session Setup SMB.
	
	- The Advanced Server \\SCRATCH receives the SMB and looks at the account name.
	
	- It looks in its local domain account database and finds a match.
	
	- \\SCRATCH then compares the SMB password to the Domain account password.
	
	- The passwords match so the "Command Completes Successfully" message is
	  generated.
	
	In these cases, the trust relationship does not come into play. If the
	Workstation had been logged on to the SCRATCH-DOMAIN, the
	NET USE x: \\NET\share command would have been successful.
	
	The real answer here is to have all workstations log on to an Advanced
	Server domain. In order to login, the user must specify their correct
	domain, account, and password. After this is done, all NET USE type
	commands will pass the correct domain, account, and password.
	Administrators should try and avoid duplicate accounts on both Windows
	NT workstations and multiple Advanced Server domains.
	
	USER: Workaround
	----------------
	
	There is one workaround that can be used in these cases. From the
	Windows NT workstation, you could carry out the following command
	
	  NET USE X: \\NET\SHARE /USER:SCRATCH-DOMAIN\USER1 PSW1
	
	where
	
	 - \\NET = The computer name of the Advanced Server being accessed.
	 - \SHARE = The share name.
	 - /USER: command line parameter that lets you specify the domain,
	   account and password that should be specified in the Session Setup
	   SMB.
	 - SCRATCH-DOMAIN = Domain name of the Advanced Server where the user
	   account resides.
	 - \USER1 = account to be validated against.
	 - PSW1 = password that matches account on the domain.
	
	For more information, type the following at a Windows NT command
	prompt:
	
	  NET USE /?
	
	NULL Domain Names
	-----------------
	
	In addition to Windows for Workgroups 3.1, other Microsoft network
	clients also send NULL Domain Names in the Session Setup SMB [x73].
	They will also exhibit the behavior described above in the example
	problem. The following is a table of how each client handles the
	Domain Name.
	
	MS Network                        Domain Name
	 Client                           Specified
	---------------------------------------------
	
	Windows for Workgroups 3.1         NULL
	
	Windows for Workgroups 3.11        Logon domain name.
	
	MS OS/2 LAN Manager 2.0, 2.1,
	and 2.2                            NULL
	
	MS-DOS LAN Manager 2.0             NULL
	
	MS-DOS LAN Manager 2.1 & 2.2   Logon domain name. * See Note below.
	(Including Windows on MS-DOS)
	
	Windows NT 3.1                     Logon domain name.
	
	
	Notes
	-----
	
	The default domain name is specified in the LANMAN.INI file on the
	"DOMAIN =" line. This can be overridden by the /DOMAIN: switch with
	the NET LOGON command.
	
	There are typically two representations for "NULL" in the SMB: A
	zero-length domain name and a one-byte domain name consisting of the
	character '?'. The Windows NT SMB server catches the '?' and
	translates it to NULL before passing it to the local security
	authority (LSA).
	
	Troubleshooting
	---------------
	
	A good tip for troubleshooting network access problems is to enable
	auditing by doing the following:
	
	1. In the User Manager for Domains window, choose Audit from the Policies menu.
	
	2. Select the Audit These Events button.
	
	3. Select the Logon and Logoff Success and Failure options.
	
	Now, anytime a network user access this server remotely, an audit
	trail will be logged in the Event Viewer. In the Event Viewer, choose
	Security from the Log menu to see the events.
	
	For information on trust relationships, pass-through authentication,
	user permissions, and domain logins, please see your Windows NT
	Advanced Server "Concepts and Planning" guide or query on the
	following words in the Microsoft Knowledge Base:
	
	  authentication and pass-through
	
	Additional query words: wfw wfwg prodnt
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbWinNTsearch kbWinNT351search kbWinNT350search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS350 kbWinNTAdvSerSearch kbWinNTAdvServ310 kbWinNTS351search kbWinNTS350search kbWinNT310Search
	Version           : 3.1 3.5 3.51 4.0
	
	=============================================================================
	

{% endraw %}
