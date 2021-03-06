---
layout: page
title: "Q151427: Server Service May Fail After Installing Network Card"
permalink: /kb/151/Q151427/
---

## Q151427: Server Service May Fail After Installing Network Card

{% raw %}

	Article: Q151427
	Product(s): Microsoft Windows NT
	Version(s): WinNT:3.51,4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 3.51, 4.0 
	- Microsoft Windows NT Server versions 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After you install network services for the first time you may see the following
	system events in the event log:
	
	  Event ID: 7023
	  Source: Service Control Manager
	  Type: Error
	  Description: The Server service terminated with the following error:
	               Not enough server storage is available to process this
	               command.
	
	  Event ID: 7001
	  Source: Service Control Manager
	  Type: Error
	  Description: The Computer browser service depends on the server
	               service which failed to start because of the following
	               error:  Not enough server storage is available to
	               process this command.
	
	When you try to start the server service at the command line using the command
	
	  NET START SERVER
	
	the following error message appears:
	
	  System error 1130 has occurred.
	  Not enough server storage is available to process this command.
	
	This problem typically occurs with computers that come from the original
	equipment manufacturer (OEM) with Windows NT and Service Pack 3 preinstalled.
	
	CAUSE
	=====
	
	This problem can occur if Windows NT is installed and the latest service pack is
	installed before any network services are installed. If the Srv.sys file is not
	present when the service pack is applied it is not updated because Update.exe
	updates only components that are installed on the Windows NT system. When
	Windows NT starts up after the network services have been installed from the
	original Windows NT CD-ROM, the original non-Service Pack 3 version of the
	Srv.sys file is used. To correctly work with the rest of the updated system
	files, the Srv.sys file must be updated to the same version as the installed
	service pack.
	
	RESOLUTION
	==========
	
	Reapply the Windows NT Service Pack.
	
	Additional query words: SP RAS Remote NIC kbfaqw2knet
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT351search kbWinNT400search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS351search
	Version           : WinNT:3.51,4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
