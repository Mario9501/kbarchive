---
layout: page
title: "Q84786: MPC MP1010 or MP4002 Error, No P-Code in Application"
permalink: /kb/084/Q84786/
---

## Q84786: MPC MP1010 or MP4002 Error, No P-Code in Application

{% raw %}

	Article: Q84786
	Product(s): Microsoft Programming Utilities
	Version(s): MS-DOS:7.0,8.0
	Operating System(s): 
	Keyword(s): kb16bitonly
	Last Modified: 30-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Make P-Code Utility for MS-DOS and Windows, versions 7.0, 8.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The MAKE P-CODE utility (MPC) is required to make a p-code executable or a
	dynamic-link library (DLL) usable. Different messages are displayed if MPC is
	run on an executable that does not contain p-code, depending on whether the .EXE
	is targeted for MS-DOS or Microsoft Windows.
	
	When MPC is run on a Windows executable or DLL that does not contain p-code, the
	following warning is produced:
	
	  warning MP4002: file contains no p-code : 'filename'
	
	However, when MPC is run on an MS-DOS executable that does not contain p-code,
	the following error is produced:
	
	  fatal error MP1010: 'filename' is not a segmented executable file
	
	MORE INFORMATION
	================
	
	Windows executables are always segmented. A typical MS-DOS executable is
	non-segmented. However, compiling an MS-DOS application with /Oq and linking
	with /PCODE produces a segmented executable. Therefore, MPC expects a segmented
	executable as input. An MS-DOS executable without p-code is not a segmented
	executable, hence the MP1010 error.
	
	The final MS-DOS p-code executable produced by MPC is not segmented, even though
	the non-runnable version produced by the linker is segmented. Therefore, the
	MP1010 error may also be generated by MPC if it is passed a runnable MS-DOS
	p-code executable as input.
	
	Additional query words: kbinf 7.00 8.00 pcode
	
	======================================================================
	Keywords          : kb16bitonly 
	Technology        : kbAudDeveloper kbZNotKeyword2 kbMakePCode kbZNotKeyword3 kbMakePcode700 kbMakePcode800
	Version           : MS-DOS:7.0,8.0
	
	=============================================================================
	

{% endraw %}
