---
layout: page
title: "Q66079: Windows Err Msg: Cannot Read From Device AUX..."
permalink: /kb/066/Q66079/
---

## Q66079: Windows Err Msg: Cannot Read From Device AUX...

{% raw %}

	Article: Q66079
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:3.0,3.0a,3.1,3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 03-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows versions 3.0, 3.0a, 3.1, 3.11 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you use the debug version of Microsoft Windows version 3.0 or 3.1 without a
	debugging terminal, your system may stop responding (hang) for a time, then the
	following error message is displayed:
	
	  Cannot read from device AUX: Retry/Cancel
	
	CAUSE
	=====
	
	The debug version of Windows is designed to wait for input from an auxiliary
	debugging terminal. If you don't have a debugging terminal attached to your
	system, the debug version of Windows cannot function as designed.
	
	WORKAROUND
	==========
	
	To prevent this error message, either connect a debugging terminal or reinstall
	the retail version of Windows.
	
	To reinstall the retail version of Windows, do the following:
	
	1. From the MS-DOS command prompt, change to the Windows directory.
	
	2. In the Windows directory, type "D2N" (without the quotation marks) and press
	  the ENTER key. D2N is a batch file that converts the debug version of Windows
	  into the normal version.
	
	MORE INFORMATION
	================
	
	The "debug" version of Windows is designed for the Windows Software Development
	Kit. This version reports errors more readily than the retail version of
	Windows. For example, bringing up the LaserJet III driver's setup screen causes
	an error to appear in the debug version of Windows, but does not generate an
	error in the retail version.
	
	The error reporting mechanism used by the debug version of Windows is a "debug
	terminal." This is a dumb terminal connected to the computer's AUX: port. When
	Windows reports an error, it immediately sends information about the error to
	the debug terminal. After Windows displays the error information, it sends a
	prompt of "Abort, Break, Ignore?" to the terminal and waits for you to type an
	appropriate command (A, B, or I).
	
	If no terminal is hooked up, or the terminal is turned off, the error codes are
	sent to a non-existent device. Also, you cannot type anything into the system
	keyboard while Windows waits for input from the debug terminal. After a period
	of time with no response from the terminal, Windows displays the "Cannot read
	device AUX" error box. Choosing Cancel causes Windows to exit, and choosing
	Retry causes Windows to wait until there is a response on the terminal. A Retry
	command can effectively lock your system if no debug terminal is connected.
	
	Additional query words: 3.00 3.0 3.0a 3.00a 3.10 3.11
	
	======================================================================
	Keywords          :  
	Technology        : kbWin3xSearch kbZNotKeyword3 kbWin300 kbWin300a kbWin310 kbWin311
	Version           : WINDOWS:3.0,3.0a,3.1,3.11
	
	=============================================================================
	

{% endraw %}
