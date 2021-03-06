---
layout: page
title: "Q158987: 32-bit NetWare Client for Windows NT Locks Services Database"
permalink: /kb/158/Q158987/
---

## Q158987: 32-bit NetWare Client for Windows NT Locks Services Database

{% raw %}

	Article: Q158987
	Product(s): Microsoft Windows NT
	Version(s): 3.5 3.51 4.0
	Operating System(s): 
	Keyword(s): kb3rdparty
	Last Modified: 10-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 3.5, 3.51, 4.0 
	- Microsoft Windows NT Server versions 3.5, 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	If you have installed Novell NetWare Client v3.5b for Windows NT and are using
	the Autoreconnect feature (installed by default), you will not be able to
	add/remove network components or administer services because the service
	database states it is locked:
	
	  STOP: The service database is locked.
	
	MORE INFORMATION
	================
	
	To unlock the services database, you must disable the NetwareAutoreconnect
	services by using Regedt32 to modify the Windows NT registry.
	
	WARNING: Using Registry Editor incorrectly can cause serious, system-wide
	problems that may require you to reinstall Windows NT to correct them. Microsoft
	cannot guarantee that any problems resulting from the use of Registry Editor can
	be solved. Use this tool at your own risk.
	
	1. Start REGEDT32.
	
	2. Find the following key:
	
	  \HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\ 
	  NetWareAutoReconnect
	
	3. After selecting the NetWareAutoReconnect key, change the value of the Start
	  entry by double-clicking the Start:REG_DWORD:0x2 and changing the value from
	  0x2 to 0x4 (automatic to disabled).
	
	4. Exit Regedt32. Restart Windows NT.
	
	WORKAROUND
	==========
	
	To work around this problem:
	
	Switch to the Microsoft Gateway Services or Client Services for NetWare
	Redirector.
	
	-or-
	
	Do not use the Autoreconnect service. Keep it disabled if you are going to use
	the Novell Requester.
	
	
	Additional query words: prodnt
	
	======================================================================
	Keywords          : kb3rdparty 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT351search kbWinNT350search kbWinNT400search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS350 kbWinNTS351search kbWinNTS350search
	Version           : 3.5 3.51 4.0
	
	=============================================================================
	

{% endraw %}
