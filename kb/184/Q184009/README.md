---
layout: page
title: "Q184009: Error Message: Unable to Save to Registry. Error Code 1243516."
permalink: /kb/184/Q184009/
---

## Q184009: Error Message: Unable to Save to Registry. Error Code 1243516.

{% raw %}

	Article: Q184009
	Product(s): Microsoft Windows NT
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kbenv kberrmsg
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Server, Enterprise Edition version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to save a copy of your registry using the System Policy Editor
	tool, you may receive the following error message:
	
	  Unable to save to registry. Error code 1243516.
	
	CAUSE
	=====
	
	This error message can occur if the Administrator account does not have full
	control permissions for one or more registry keys.
	
	RESOLUTION
	==========
	
	You may be able to resolve this problem by restoring the affected registry file.
	To do so, follow these steps:
	
	1. Start your computer using the Windows NT Setup floppy disks.
	
	2. In the Windows NT Workstation Setup screen, press R (to repair).
	
	3. Clear all check boxes except for the Inspect Registry Files check box. To
	  clear a check box, select it, and then press ENTER.
	
	4. Select Continue (Perform Selected Tasks), and then press ENTER.
	
	5. When you are prompted to select the registry files to repair, select the
	  System (System Configuration) check box, and then press ENTER to add a check
	  mark.
	
	6. Select Continue (Perform Selected Tasks), press ENTER, and then follow the
	  instructions on your screen.
	
	  NOTE: If your computer contains hardware that requires third-party drivers,
	  you may have to install the drivers again. Also, you may have to reconfigure
	  the settings for some hardware.
	
	7. Restart your computer, and then try to save your registry again using the
	  System Policy Editor tool.
	
	If you receive the same error message, the Software or Security registry file may
	be causing the problem. To determine if this is the case, repeat the steps, and
	select the Software (Software Information) check box in step 5. If you still
	receive the error message when you try to save your registry, repeat the steps,
	and select the "Security (Security Policy) and SAM (User Accounts Database)"
	check box in step 5.
	
	NOTE: If you select the Software registry file, you may have to install some
	software again. If you select the Security registry file, you must re-create all
	user accounts.
	
	MORE INFORMATION
	================
	
	These steps are intended to provide a way to restore the necessary permissions
	for affected registry keys. If you attempt to change the security permissions
	for the registry keys using Registry Editor, the problem still occurs. Using the
	steps in this article can prevent having to reinstall Windows NT.
	
	For additional information about using Windows NT Setup floppy disks, please see
	the following article in the Microsoft Knowledge Base:
	
	  ARTICLE-ID: Q131735
	  TITLE : How to Create Windows NT Boot Floppy Disks
	
	NOTE: This does not backup the entire registry. It only backs up the registry
	keys that are impacted by the System Policy Editor.
	
	Additional query words: erd
	
	======================================================================
	Keywords          : kbenv kberrmsg 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400 kbWinNTS400search kbWinNTS400
	Version           : :4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
