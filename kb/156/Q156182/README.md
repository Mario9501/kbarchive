---
layout: page
title: "Q156182: XCLN: Changing Windows NT 4.0 Password in Microsoft Exchange"
permalink: /kb/156/Q156182/
---

## Q156182: XCLN: Changing Windows NT 4.0 Password in Microsoft Exchange

{% raw %}

	Article: Q156182
	Product(s): Microsoft Exchange
	Version(s): 4.0,5.0,8.0,8.1,8.2,8.2.1,8.2.2
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 30-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 4.0, 5.0 
	- the operating system: Microsoft Windows NT 4.0 
	- Microsoft Exchange Macintosh client, versions 4.0, 5.0 
	- Microsoft Outlook for Macintosh, Exchange Server Edition, versions 8.0, 8.1, 8.2, 8.2.1, 8.2.2 
	- Microsoft Outlook 2001 for Mac 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A Windows NT 4.0 password cannot be changed from the Microsoft Exchange
	Macintosh client. The scenario is as follows (this is the same for Banyan Vines
	TCP/IP clients):
	
	You are using the Microsoft Exchange Macintosh client and attempting to change
	the Windows NT password by clicking Options on the Tools menu. On the Exchange
	Server tab, you click Password. After you type all the information and click OK,
	the following message appears:
	
	  Please enter the AppleTalk Zone of your Microsoft Windows NT Primary
	  Domain Controller.
	
	After you enter the Apple-Talk zone and click OK, the following message appears:
	
	  The Windows NT Domain password could not be changed. A required action was
	  not successful due to an unspecified error.
	
	As a result, the password is not changed.
	
	RESOLUTION
	==========
	
	In order for the Microsoft Exchange Macintosh client to change the Windows NT
	domain password, the registry must be modified as follows:
	
	WARNING: Using Registry Editor incorrectly can cause serious problems that may
	require you to reinstall Windows NT. Microsoft cannot guarantee that problems
	resulting from the incorrect use of Registry Editor can be solved. Use Registry
	Editor at your own risk.
	
	1. On the Windows NT Primary Domain Controller (PDC), start Registry Editor,
	  regedt32.exe (regedit.exe in Windows NT 4.0 will not work) to edit the PDC's
	  Registry.
	
	2. Under the HKEY_LOCAL_MACHINE subtree, go to the following subkey:
	
	     SYSTEM\CurrentControlSet\Control\Lsa
	
	3. Select Lsa to highlight it.
	
	4. On the Edit menu, click Add Value.
	
	5. Make one of the changes listed below, depending on whether AppleTalk or
	  TCP\IP protocol will be used:
	
	  For password support using AppleTalk protocol, enter:
	
	     Value Name:  AppletalkClientSupport
	     Data Type:  REG_DWORD
	     DWORD Editor Data: 1
	
	  -OR-
	
	  For password support using TCP/IP protocol, enter:
	
	     Value Name:  TCPIPClientSupport
	     Data Type:  REG_DWORD
	     DWORD Editor Data: 1
	
	6. Restart the primary domain controller (PDC).
	
	7. From Windows NT User Manager for Domains, select a user account of a
	  Microsoft Exchange Macintosh client user. On the Policies menu, click
	  Account. At the bottom of the Account Policy dialog box is the check box
	  "Users must log on in order to change password". Make sure this check box is
	  cleared.
	
	8. If using TCP/IP as connecting protocol, the client must have a hosts file or
	  Domain Name Service (DNS) with entries for both Microsoft Exchange Server and
	  the Windows NT PDC. (The A and CNAME records)
	
	With the above configuration in place, you can now change the Windows NT domain
	password using the Microsoft Exchange Macintosh Client as follows:
	
	1. On the Tools menu, click Options.
	
	2. On the Exchange Server tab, click the Password button.
	
	3. Type the information and click OK. A message appears stating:
	
	     Your password has been changed.
	
	  Future log on process(es) to domain resources will use the new password.
	
	REFERENCES
	==========
	
	For additional information, please see the following articles in the Microsoft
	Knowledge Base:
	
	  Q127943 Mac Client Can't Logon Because Password Has Expired
	
	  Q153213 XCLN: Can't Change Windows NT 3.51 Password w/ AppleTalk
	
	  Q140641 Updated Samsrv.dll Supports AppleTalk and Banyan Vines Clients
	
	
	
	Additional query words: chooser AppleShare Mac BDC
	
	======================================================================
	Keywords          : kbusage 
	Technology        : kbHWMAC kbOSMAC kbOSWinSearch kbOSWinNT400 kbExchangeSearch kbExchange500 kbExchange400 kbExchangeClientSearch kbZNotKeyword2 kbOutlook2001Search kbZNotKeyword3 kbOutlookMacSearch kbOSWinNTSearch kbExchange500Mac kbExchange400Mac kbOutlook800Mac kbOutlook810Mac kbOutlook820Mac kbOutlook821Mac kbOutlook822Mac
	Version           : :4.0,5.0,8.0,8.1,8.2,8.2.1,8.2.2
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
