---
layout: page
title: "Q104360: PC Win: New Mail Notification Using a Custom Command"
permalink: /kb/104/Q104360/
---

## Q104360: PC Win: New Mail Notification Using a Custom Command

{% raw %}

	Article: Q104360
	Product(s): Microsoft Mail For PC Networks
	Version(s): WINDOWS:3.0,3.0b,3.2
	Operating System(s): 
	Keyword(s): 
	Last Modified: 29-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail for Windows, versions 3.0, 3.0b, 3.2 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Versions 3.0 and later of Microsoft Mail for Windows provide the ability to
	develop custom commands. Chapter 1 in the "Technical Reference" describes how to
	define custom commands.
	
	You can define a custom command so that whenever Microsoft Mail is minimized or
	is in the background on the screen and new mail arrives, the Mail window is
	brought to the foreground. You can use this feature as a means of new mail
	notification.
	
	Custom commands are defined in the MSMAIL.INI file (which is usually located in
	the Windows directory), in a section titled [Custom Commands].
	
	If this section does not exist, you can create it by adding the following new
	section header:
	
	  [Custom Commands]
	
	The custom command for new mail notification should be after the [Custom
	Commands] line and is as follows
	
	  notify=3.0;;;;appexec.dll;<path>\msmail.exe;0010000000000000;
	
	where <path> is the complete path to the MSMAIL.EXE file. "Notify" is a
	label and can be replaced by any other text string. The APPEXEC.DLL file is
	usually not copied to the local computer during the setup process.
	
	APPEXEC.DLL was not shipped with version 3.0. However, it was included with
	versions 3.0b and 3.2.
	
	With Mail 3.0b, APPEXEC.DLL is located on the Messaging Applications Development
	Tools disk, in the MAILEXTS subdirectory.
	
	With Mail 3.2, APPEXEC.DLL is located on the Technical Reference Server Programs
	disk, in the MAILEXTS subdirectory.
	
	You should copy the APPEXEC.DLL file to the Windows subdirectory.
	
	NOTE: Mail must be running for this method of notification to work. Mail can be
	either in the background or minimized. If you are in an MS-DOS window or if you
	are running an MS-DOS application, there will be a change of context and mail
	will be brought to the foreground.
	
	MORE INFORMATION
	================
	
	The information above is for a private custom command. To share this custom
	command with other users, you need to define a shared command. To do this, you
	must have a file named SHARED.INI in a shared directory on a server. Then
	perform the following steps:
	
	1. If the [Custom Commands] section does not exist in this file, create that
	  section and then add the above custom command to the [Custom Commands]
	  section.
	
	2. Copy the APPEXEC.DLL file to this shared directory.
	
	3. On each user's local MSMAIL.INI file, in the [Microsoft Mail] section, add
	  the following line:
	
	  SharedExtensionsDir=<Path to the Shared directory on the server>
	
	  You can specify the path in UNC notation (for example,
	  \\<Server_name>\<share_name>) or you can specify the path using a
	  drive name (for example, d:\mailexts).
	
	For more detailed information on creating shared custom commands, refer to
	Chapter 1 of the Microsoft Mail for PC Networks "Technical Reference."
	
	Additional query words: 3.00 3.00b 3.20
	
	======================================================================
	Keywords          :  
	Technology        : kbMailSearch kbZNotKeyword3 kbMail300 kbMail320 kbMail300b
	Version           : WINDOWS:3.0,3.0b,3.2
	
	=============================================================================
	

{% endraw %}
