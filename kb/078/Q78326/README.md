---
layout: page
title: "Q78326: Real Mode Not Supported by Windows 3.1"
permalink: /kb/078/Q78326/
---

## Q78326: Real Mode Not Supported by Windows 3.1

{% raw %}

	Article: Q78326
	Product(s): Microsoft Windows Software Development Kit
	Version(s): WINDOWS:3.1
	Operating System(s): 
	Keyword(s): kb16bitonly
	Last Modified: 06-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows Software Development Kit (SDK) 3.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Support for real mode has been removed from Windows 3.1. Many applications
	designed for Windows 3.0 do not support real mode. The reasons behind this trend
	toward protected mode include superior memory management and smaller, faster
	application code.
	
	MORE INFORMATION
	================
	
	The remainder of this article lists the advantages and disadvantages of removing
	support for real mode from applications.
	
	Advantages of Removing Real Mode Support
	----------------------------------------
	
	1. Protected mode code is smaller, cleaner, and more maintainable. These factors
	  lead to a faster, more responsive, more reliable, system. Code is smaller and
	  cleaner for the following reasons:
	
	  a. The 286 and higher processors can track memory locations in hardware,
	     which makes locking and unlocking memory objects unnecessary. An object
	     can be locked once when it is allocated and unlocked just prior to being
	     freed. Because the object can move in memory even when it is locked, it is
	     not necessary to bracket each access to an object with lock and unlock
	     calls.
	
	  b. Far functions can use simplified function prolog and epilog code. For more
	     information on this aspect of protected mode, query on the following
	     words:
	
	  " prod(winsdk) and protected and streamlined " (without the quotation marks)
	
	  c. Because protected mode code is restricted to running on 286 and higher
	     processors, the Microsoft C Compiler -G2 switch can be used to generate
	     smaller and faster application code.
	
	2. Protected mode (both standard and enhanced mode) breaks the "640K barrier."
	  Furthermore, under enhanced mode, Windows uses paged virtual memory to expand
	  available memory by using the system hard disk as a swapping device. The
	  large address space allows applications to have more code and data and allows
	  users to run more applications.
	
	3. Testing is easier because there are fewer Windows modes to test. To fully
	  test a product that runs under real mode, five separate modes must be tested.
	  Real mode itself contributes three of those modes: real mode with no expanded
	  memory, real mode using the small-frame Expanded Memory Specification (EMS)
	  and real mode using the large- frame EMS. The other two modes are standard
	  mode and enhanced mode. Because support for real mode has been eliminated,
	  the same amount of testing effort can concentrate on producing a better
	  product. It also provides an opportunity to develop and test additional
	  enhancements. For more information on EMS, query on the following words:
	
	  " prod(winsdk) and ems and developers " (without the quotation marks)
	
	4. Based on a survey of Windows developers, most developers are targeting only
	  protected mode because Windows performance on 8086- based and 8088-based
	  machines is not satisfactory. Furthermore, these machines cannot address more
	  than 640K of RAM.
	
	5. "Wild writes," write-accesses to memory that incorrectly modify a memory
	  location, can frequently be detected in protected mode through the mechanism
	  of a GP-fault (an unrecoverable application error). It is not possible to
	  detect these errors under real mode. These GP-faults provide information
	  about application bugs before the application is released.
	
	For the reasons mentioned above, Microsoft is removing support for real mode from
	Windows 3.1. For these same reasons, many developers have also removed support
	for real mode from applications developed for Windows 3.0. Applications that are
	written to support only protected mode should be marked with the Resource
	Compiler's -T switch to prevent the application from loading in real mode.
	
	Removing support for real mode also benefits the end user because applications
	run faster and are more reliable. While small applications run quickly in real
	mode, larger applications run slowly. However, in protected mode, large
	applications also run quickly. A collection of large and small applications can
	be run simultaneously without any loss in speed. For example, when more
	applications are running simultaneously than can fit in the physical memory
	installed in the system, the paging mechanism (only available in enhanced mode)
	intelligently manages virtual memory to keep the most-frequently used memory
	pages in physical memory. This management speeds up the system.
	
	Disadvantages of Removing Real Mode Support
	-------------------------------------------
	
	1. The installed base of 8088-based and 8086-based machines cannot use the
	  software.
	
	2. Code that performs segment arithmetic cannot be used in protected mode.
	  Therefore, some drivers and MS-DOS programs that run in real mode must be
	  rewritten for protected mode, or they cannot be run under Windows 3.1.
	
	Additional query words: 3.10 no32bit
	
	======================================================================
	Keywords          : kb16bitonly 
	Technology        : kbAudDeveloper kbWin3xSearch kbSDKSearch kbWinSDKSearch kbWinSDK310
	Version           : WINDOWS:3.1
	
	=============================================================================
	

{% endraw %}
