---
layout: page
title: "Q318730: &quot;??_U@YAPAXI@Z Not Located in Msvcrt.dll&quot; Err Msg at Startup"
permalink: /kb/318/Q318730/
---

## Q318730: &quot;??_U@YAPAXI@Z Not Located in Msvcrt.dll&quot; Err Msg at Startup

{% raw %}

	Article: Q318730
	Product(s): Microsoft Windows NT
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kberrmsg
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	- Microsoft Windows NT Workstation version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you start your Windows NT 4.0-based computer, you may receive an error
	message similar to the following:
	
	  rpcss.exe
	
	  The procedure entry point ??_U@YAPAXI@Z could not be located in msvcrt.dll
	
	-or-
	
	When you try to start a program, you may receive an error message similar to the
	following:
	
	  <Application>.exe - Entry Point not Found
	
	  The procedure entry point ??_U@YAPAXI@Z could not be located in the Dynamic
	  Link Library MSVCRT.DLL
	
	CAUSE
	=====
	
	This behavior may occur if you install a third-party program that replaces some
	of the Windows NT 4.0 dynamic-link library (DLL) files with those of a different
	version.
	
	This behavior occurs when mismatched DLL files try to reference a function in
	Msvcrt.dll.
	
	RESOLUTION
	==========
	
	To resolve this issue, replace the following DLL files with new copies from a
	Windows NT 4.0 computer that is updated to the same service pack level and that
	is running the same version of Microsoft Internet Explorer as the Windows NT
	installation on which you experience this issue:
	
	  Msvcrt.dll
	  Msvcirt.dll
	  Msvcrt20.dll
	  Msvcrt40.dll
	
	To do this, use one of the following methods, as appropriate to your situation.
	
	Method 1: Contact Microsoft to Obtain Copies of the DLL Files
	-------------------------------------------------------------
	
	1. Contact Microsoft to obtain copies of the four DLL files mentioned at the
	  beginning of the "Resolution" section of this article.
	
	  For information about how to so this, browse to the following Microsoft Web
	  site:
	
	  http://support.microsoft.com
	
	2. Copy the replacement DLL files to the %<SYSTEM_ROOT>%\System32 folder
	  of your Windows NT installation.
	
	Method 2: Perform a Parallel Windows Installation
	-------------------------------------------------
	
	1. If you do not have access to another computer running Windows NT 4.0, install
	  a new copy of Windows NT 4.0 to a different folder on your computer.
	
	For additional information about how to do this, click the article numbers below
	to view the articles in the Microsoft Knowledge Base:
	
	  Q259003 How and Why to Perform a Parallel Installation of Windows NT 4.0
	
	  Q244378 System Cleanup After a Parallel Installation of Windows NT 4.0
	
	2. Log on to the new Windows installation, and then install the same service
	  pack as that of the installation with which you experience this problem. To
	  obtain the latest service pack for Windows NT 4.0, browse to the following
	  Microsoft Web site:
	
	  http://www.microsoft.com/ntserver/nts/downloads/recommended/SP6/allSP6.asp
	
	3. Install the same version of Internet Explorer as that of the Windows
	  installation with which you experience this problem. To obtain the latest
	  version of Internet Explorer, browse to the following Microsoft Web site:
	
	  http://www.microsoft.com/windows/ie
	
	  NOTE: If you cannot update the new Windows installation with the same version
	  of Internet Explorer as that of the original Windows installation, install
	  the latest version of Internet Explorer. Then, after you replace the DLL
	  files in step 4, update the original Windows installation to the latest
	  version of Internet Explorer.
	
	4. Start Windows Explorer, and then copy the following files from the
	  %<SYSTEM_ROOT>%\System32 folder on the new Windows installation to the
	  %<SYSTEM_ROOT>%\System32 folder of the Windows installation with which
	  you experience this issue:
	
	  Msvcrt.dll
	  Msvcirt.dll
	  Msvcrt20.dll
	  Msvcrt40.dll
	
	5. Restart the computer, and then log on to the original Windows installation.
	
	Additional query words:
	
	======================================================================
	Keywords          : kberrmsg 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbNTTermServ400 kbNTTermServSearch
	Version           : :4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
