---
layout: page
title: "Q82216: Command Piped in Root Directory May Hang Machine"
permalink: /kb/082/Q82216/
---

## Q82216: Command Piped in Root Directory May Hang Machine

{% raw %}

	Article: Q82216
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:5.0,5.0a,6.0,6.2,6.21,6.22; WINDOWS:3.0,3.0a,3.1,3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 19-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 5.0, 5.0a, 6.0, 6.2, 6.21, 6.22 
	- Microsoft Windows versions 3.0, 3.0a, 3.1, 3.11 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If you run an MS-DOS command in a root directory that contains the maximum
	allowable number of directory entries, and redirect the output by using a pipe
	character (|), your system may stop responding (hang).
	
	CAUSE
	=====
	
	MS-DOS provides the means to direct the output of one command as input to
	another using a redirection technique known as "piping." Because MS-DOS is a
	single-tasking environment, these pipes are created via temporary files on
	disk.
	
	MS-DOS checks for the presence of an environment variable called TEMP specifying
	the drive and directory where such temporary files should be placed. If no TEMP
	variable or directory exists, MS-DOS uses the current directory.
	
	If the output from one command is piped to another when the current directory is
	a root directory that already contains the maximum number of directory entries
	(for example, 512 files for fixed disks,) the inability to create the temporary
	files may stop (hang) the machine.
	
	RESOLUTION
	==========
	
	To eliminate this problem, do the following:
	
	- Delete or move some files from the root directory to create space for
	  additional directory entries.
	
	-or-
	
	- Create an X:\TEMP directory and place a SET TEMP=X:\TEMP statement in the
	  AUTOEXEC.BAT file. The temporary files created by the pipe are then placed in
	  the X:\TEMP directory, where X: is a valid MS-DOS logical drive.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in MS-DOS. We are researching this
	problem and will post new information here as it becomes available.
	
	REFERENCES
	==========
	
	For additional information on command redirection, refer to the "Microsoft
	MS-DOS User's Guide and Reference," for version 5.0.
	
	For additional information on the limits of the root directory with regard to the
	number of directory entries, query on the following words in the Microsoft
	Knowledge Base:
	
	  " directory and limit and entries " (without the quotation marks)
	
	Additional query words: 6.22 5.00 5.00a 6.00 6.20 lock up lockup 3.00 3.00a 3.10 3.11
	
	======================================================================
	Keywords          :  
	Technology        : kbWin3xSearch kbZNotKeyword3 kbWin300 kbWin300a kbWin310 kbWin311 kbMSDOSSearch kbMSDOS621 kbMSDOS622 kbMSDOS620 kbMSDOS600 kbMSDOS500 kbMSDOS500a
	Version           : MS-DOS:5.0,5.0a,6.0,6.2,6.21,6.22; WINDOWS:3.0,3.0a,3.1,3.11
	
	=============================================================================
	

{% endraw %}
