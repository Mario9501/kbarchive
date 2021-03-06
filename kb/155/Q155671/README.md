---
layout: page
title: "Q155671: DBWEB: NT 3.51 SP4 Doesn't Restart After Installing dbWeb1.1a"
permalink: /kb/155/Q155671/
---

## Q155671: DBWEB: NT 3.51 SP4 Doesn't Restart After Installing dbWeb1.1a

{% raw %}

	Article: Q155671
	Product(s): Microsoft Access Distribution Kit
	Version(s): WINDOWS:1.1
	Operating System(s): 
	Keyword(s): kberrmsg
	Last Modified: 24-JUL-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft dbWeb, version 1.1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Windows NT Server 3.51 with Service Pack 4 does not restart after you install
	Microsoft dbWeb 1.1a. A blue screen appears with the message:
	
	    SESSION3_INITIALIZATION_FAILED
	
	CAUSE
	=====
	
	The initial release of dbWeb 1.1a contained a Setup program that failed to copy
	the Microsoft Windows NT 3.51 system file Smss.exe back onto the hard drive
	after removing the original Smss.exe from the \Winnt\System32 folder.
	
	RESOLUTION
	==========
	
	Rerun Windows NT Server Setup and initiate the emergency repair process in order
	to copy Smss.exe back to the \Winnt\System32 directory. To do this, you need the
	original Windows NT Server installation disks and CD-ROM.
	
	You can use an emergency repair disk with Setup, but it is not required. If you
	do not supply an emergency repair disk, Setup will attempt to use the repair
	directory on the hard drive. An emergency repair disk created for one computer
	will not work on another computer. Use the following steps to rerun Setup and
	initiate the emergency repair process.
	
	NOTE: The following steps assume that Windows NT is installed in a folder called
	\Winnt. Change the folder name as appropriate for your computer.
	
	1. Restart the computer using the Windows NT Setup startup disk. When prompted,
	  insert Windows NT Setup disk 2.
	
	2. When the Windows NT Setup screen appears, type R to initiate the emergency
	  repair process. Follow the instructions on screen to clear and select from
	  the following:
	
	     [ ] Inspect registry files
	     [ ] Inspect startup environment
	     [X] Verify Windows NT system files
	     [ ] Inspect boot sector
	     Continue (perform selected tasks)
	
	  Select Verify Windows NT system files.
	
	3. Select Continue (perform selected tasks) and press ENTER.
	
	4. Press ENTER to continue detection of mass storage devices in your computer.
	  When prompted, insert Setup disk 3 and press ENTER.
	
	5. Press ENTER to continue without specifying additional mass storage devices in
	  your computer. At the next screen, press ENTER to continue.
	
	6. When prompted, insert your Emergency Repair disk and press ENTER. If you do
	  not have an Emergency Repair disk, Windows NT will use the Repair folder on
	  your hard drive.
	
	7. Setup asks if you want your hard disks examined for corruption. Because the
	  purpose of this repair is to copy Smss.exe back into the \Winnt\System32
	  folder, you can press ESC to skip disk verification.
	
	8. The emergency repair process will check the date and time of files on your
	  computer to determine if they are the original files copied by the Windows NT
	  Server installation. Because Service Pack 4 is installed, Setup prompts you
	  to replace many files, but Smss.exe is the only file you need to copy. When
	  Setup prompts you to replace a file, press ESC to bypass the replacement for
	  all files except Smss.exe.
	
	9. Press ENTER to restart your computer.
	
	MORE INFORMATION
	================
	
	A setup program sometimes attempts to upgrade system files. Because it cannot
	overwrite files when they are in use, Setup copies the new files as temporary
	files to a temporary location, and creates new Windows registry entries
	detailing which files need to be deleted or overwritten. When you restart your
	computer, Smss.exe reads the registry files and performs those actions.
	
	The version of Smss.exe in Windows NT 3.51 Service Pack 4 does not perform its
	task correctly, so the dbWeb 1.1 and 1.1a Setup program compares the date and
	time on the current Smss.exe file to the one in its compressed archive. If the
	latter file has a more recent date and time, the Setup program prompts you
	whether you want to install a patch to NT 3.51 SP4.
	
	This works fine in the initial release of dbWeb 1.1. However, with dbWeb 1.1a,
	the Smss.exe file location in the Setup program's compressed archive was changed
	because it caused a problem during the digital signing process (necessary for
	all downloads from the www.microsoft.com Internet address). The setup script,
	however, does not reflect the change in location, and it expects to find
	Smss.exe in its old location. During setup, if you choose to install the patch
	to Windows NT 3.51 SP4, the dbWeb 1.1a Setup program schedules the renaming of
	the old Smss.exe, but does not copy the new Smss.exe because it cannot find it
	in its compressed archive.
	
	Upon restart, Windows NT cannot find Smss.exe, which is necessary for startup, so
	it displays the STOP message, "SESSION3_INITIALIZATION_FAILED."
	
	Additional query words:
	
	======================================================================
	Keywords          : kberrmsg 
	Technology        : kbAudDeveloper kbdbWebSearch kbdbWeb110
	Version           : WINDOWS:1.1
	Hardware          : x86
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
