---
layout: page
title: "Q161979: Encarta: How to Disable the Ability to Start Programs"
permalink: /kb/161/Q161979/
---

## Q161979: Encarta: How to Disable the Ability to Start Programs

{% raw %}

	Article: Q161979
	Product(s): Microsoft Home Multimedia Titles
	Version(s): WINDOWS:
	Operating System(s): 
	Keyword(s): kbenv kbui kbimu
	Last Modified: 12-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Encarta Encyclopedia 97 Deluxe for Windows 
	- Microsoft Encarta 97 Encyclopedia for Windows 
	- Microsoft Encarta 98 Encyclopedia for Windows 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about editing the registry.
	Before you edit the registry, you should first make a backup copy of the
	registry files (System.dat and User.dat). Both are hidden files in the
	Windows folder.
	
	SUMMARY
	=======
	
	It may be necessary for you to prevent access to executable programs on your
	computer. For example, you can disable the Run command in Windows Explorer to
	restrict access to files and folders. If the Run command is disabled, you cannot
	locate and execute programs.
	
	MORE INFORMATION
	================
	
	In addition to a Run command, certain programs have other methods of starting
	executable programs. Microsoft Encarta Encyclopedia 1997 and 1998 editions
	provide two ways to start an executable program.
	
	The "Choose Web Browser" and "Choose Word Processor" options allow you to
	customize Encarta Encyclopedia so that a particular program starts (this can
	include files such as Command.com, Progman.exe, or Explorer.exe) You are also
	able to start Msinfo.exe, located in the About box. This feature contains the
	Run command on the File menu.
	
	You can configure Encarta Encyclopedia to restrict these options without
	affecting the program's functionality. To accomplish this, use the appropriate
	method for your version of Windows.
	
	NOTE: The ability to restrict a user from customizing which program starts from
	within Encarta was added to the 1997 edition of Encarta Encyclopedia. Previous
	editions of Encarta Encyclopedia enabled you to customize which program starts,
	but you could not prevent a user from changing the settings.
	
	
	Windows 3.x
	-----------
	
	NOTE: Encarta 98 Encyclopedia will not run in Microsoft Windows 3.x.
	
	In Windows 3.x, follow these steps to disable the ability to run executable
	programs:
	
	1. Open the Encarta.ini file in a word processor program, such as Notepad or
	  Write.
	
	2. In the [97Options] section, type the following line:
	
	     AllowAppSelection=0
	
	3. Save the file, quit the word processor program, and then restart Encarta.
	
	Windows 95/98
	-------------
	
	In Windows 95/98, follow these steps to disable the ability to run executable
	programs:
	
	For information about how to edit the registry, view the Changing Keys And Values
	online Help topic in Registry Editor (Regedit.exe). Note that you should make a
	backup copy of the registry files (System.dat and User.dat) before you edit the
	registry.
	
	WARNING: Using Registry Editor incorrectly can cause serious problems that may
	require you to reinstall Windows 95. Microsoft cannot guarantee that problems
	resulting from the incorrect use of Registry Editor can be solved. Use Registry
	Editor at your own risk.
	
	1. Use Registry Editor to open the appropriate key for your version of Encarta:
	
	     Encarta 97 Encyclopedia
	     -----------------------
	
	        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Reference\Encarta
	        Encyclopedia\97
	
	     Encarta 98 Encyclopedia
	     -----------------------
	
	        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Reference\Encarta
	        Encyclopedia\98
	
	2. Click Edit, point to New, and then click DWORD Value.
	
	3. Type the following line, and then press ENTER:
	
	     AllowAppSelection
	
	4. Quit Registry Editor.
	
	5. Restart Encarta Encyclopedia.
	
	NOTE: The Choose Web Browser and Choose Word Processor buttons, located in the
	Settings screen, should be disabled. The System Information button, located in
	the About Encarta screen, should also be disabled.
	
	Additional query words: multi multi-media media mm security
	
	======================================================================
	Keywords          : kbenv kbui kbimu 
	Technology        : kbHomeProdSearch kbHomeMMsearch kbEncartaSearch kbEncartaEncycSearch kbEncartaEnCyc1997 kbEncartaEnCyc1997Del kbEncartaEnCyc1998
	Version           : WINDOWS:
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
