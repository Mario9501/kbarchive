---
layout: page
title: "Q133106: FORTRAN PowerStation 32 QUICKWIN.TXT"
permalink: /kb/133/Q133106/
---

## Q133106: FORTRAN PowerStation 32 QUICKWIN.TXT

{% raw %}

	Article: Q133106
	Product(s): Microsoft Fortran Compiler
	Version(s): 1.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 02-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Fortran Powerstation 32 for Windows NT, version 1.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The following information is from the Microsoft FORTRAN PowerStation 32
	QUICKWIN.TXT file located in the \FPSNT\README directory.
	
	This file has three parts:
	
	    Part     Contents
	    ----     --------
	     1       Writing QuickWin Programs
	     2       Running QuickWin Programs
	     3       Differences in QuickWin
	
	MORE INFORMATION
	================
	
	================< Part 1: Writing QuickWin Programs >==================
	
	STOP and PAUSE use Default Window
	---------------------------------
	The STOP and PAUSE statements use the default window (typically the
	Graphic1 window) under QuickWin. Because the default window has
	IOFOCUS=.FALSE., this window does not have the focus when one of
	these statements is executed. This can cause confusion if another
	window is on top because the STOP or PAUSE output is not visible.
	
	A workaround is to change the focus to the default window before
	executing one of these commands (with FOCUSQQ(0)).
	
	Access to True Windows Handles
	------------------------------
	Some Win32 API calls require the true Windows handle to the window to
	do work upon. You can obtain these handles by calling GETHANDLEFRAMEQQ,
	GETHANDLECLIENTQQ, and GETHANDLECHILDQQ, which return the Windows
	handle to the frame, client area, and child window, respectively. Note
	that the Windows handle is different from the QuickWin handle (provided
	by a call to GETHANDLEQQ).
	
	All three routines return type INTEGER*4. Only GETHANDLECHILDQQ takes
	an argument, which is the QuickWin handle returned by GETHANDLEQQ for a
	particular child window. All three have interfaces in FLIB.FI and
	FLIB.FD, two libraries that are included in Microsoft FORTRAN.
	
	For information on using the Win32 API, consult the Win32 API
	Programmer's Reference, available from Microsoft Press.
	
	An example program:
	
	  INCLUDE 'flib.fi'
	  PROGRAM Windows_Handle_Sample
	  INCLUDE 'flib.fd'
	
	  OPEN(unit=20,file='USER')
	  WRITE (20,*) 'This opens the Window'
	
	  WRITE(*,10) GETHANDLEFRAMEQQ()
	  WRITE(*,20) GETHANDLECLIENTQQ()
	  WRITE(*,30) GETHANDLECHILDQQ(GETHANDLEQQ(6))
	  WRITE(*,40) GETHANDLECHILDQQ(GETHANDLEQQ(20))
	  WRITE(*,50) GETHANDLECHILDQQ(GETHANDLEQQ(30))
	
	10     FORMAT(' Frame Handle:          ',Z8)
	20    FORMAT(' Client Area:           ',Z8)
	30   FORMAT(' Unit 6:                ',Z8)
	40   FORMAT(' Unit 20:               ',Z8)
	50   FORMAT(' Unit 30 (returns -1):  ',Z8)      ! -1 for bad unit
	
	  END
	
	================< Part 2: Running QuickWin Programs >==================
	
	Using DLLs with QuickWin
	------------------------
	Driver switches /MD and /LD are incompatible with /MW (QuickWin),
	because QuickWin must be linked with a static library (via /ML or /MT).
	When using DLLs with QuickWin, there will be two copies of the run-time
	libraries present in the executable: one for QuickWin and one for the
	DLL.  For this reason, file units in QuickWin cannot be shared with
	file units in DLL libraries, and therefore DLLs cannot write to
	QuickWin child windows.  Console I/O is also not possible from the DLL
	because there is no console. However, file I/O from the DLL is allowed.
	
	Size-to-Fit/Full-Screen Delay
	-----------------------------
	On slower computers, switching between Size-To-Fit and Full-Screen modes
	in a FORTRAN application takes some time.  During this interval, the
	cursor disappears.
	
	Unresponsive QuickWin Menus and Windows
	---------------------------------------
	The main thread (the one which executes the main program of a QuickWin
	application) is responsible for handling the Windows messages for the
	application, through imbedded calls to YIELDQQ.  Therefore, if this
	thread is blocked for any reason, the menu response, resizing, and even
	repainting will not happen until the main thread is no longer blocked.
	Threads can be blocked for a number of reasons, such as for a breakpoint
	in the debugger, by executing a SLEEPQQ, or by executing a
	WAITFORMULTIPLEOBJECTS when doing multithreading.
	
	Greater Than 256 Color Display Drivers
	--------------------------------------
	QuickWin can only support up to 256 colors in a palette, even if the
	underlying display driver can handle more colors than this.
	
	Menus and Windows Appear at First Graphics Call
	-----------------------------------------------
	The menu of a QuickWin application will not appear until the first
	graphics call or SETWINDOWCONFIG is called. Until then, only the File
	menu item will be present. Child windows will also not be displayed
	until a graphics call or SETWINDOWCONFIG for that particular window.
	
	Copy and Paste under QuickWin
	----------------------------
	Because QuickWin windows now support both text and graphics, performing
	a Copy command from the Edit menu copies a bitmap of the currently
	active window. The Cut command does not cut text, even if there is only
	text in the window. The Paste command does paste text to be read by the
	READ statement.
	
	Occasional ARC drawing problem
	------------------------------
	The ARC (and ARC_W) routine may occasionally fail to draw some of the
	pixels adjacent to the arc end points (the end points will be set in
	all cases). If using FLOODFILL, this gap can cause the fill to
	"escape." In many cases, you can use the PIE routine instead because
	it does not exhibit this problem.
	
	=================< Part 3: Differences in QuickWin >===================
	
	Differences between FPSNT and FPS/DOS (F32)
	-------------------------------------------
	
	1) FPS NT  INTEGER*4 FUNCTION  SAVEIMAGE (fname,x1,y1,x2,y2)
	          INTEGER*4 x1,y1,x2,y2
	  F32     INTEGER*2 FUNCTION  SAVEIMAGE (fname,x1,y1,x2,y2)
	          INTEGER*2 x1,y1,x2,y2
	
	2) FPS NT  INTEGER*4 FUNCTION  SAVEIMAGE_W(fname,wx1,wy1,wx2,wy2)
	          REAL*8 wx1,wy1,wx2,wy2
	  F32     INTEGER*2 FUNCTION  SAVEIMAGE_W(fname,wx1,wy1,wx2,wy2)
	          REAL*4 wx1,wy1,wx2,wy2
	
	3) FPS NT  INTEGER*4 FUNCTION   LOADIMAGE(fname,x,y)
	          INTEGER*4 x,y
	  F32     INTEGER*2 FUNCTION   LOADIMAGE(fname,x,y)
	          INTEGER*2 x,y
	
	4) FPS NT  INTEGER*4 FUNCTION   LOADIMAGE_W(fname,wx,wy)
	          REAL*8 wx,wy
	  F32     INTEGER*2 FUNCTION   LOADIMAGE_W(fname,wx,xy)
	          REAL*4 wx,wy
	
	These graphics functions did not exist in Fortran 5.1
	
	(This note does not contain the full interface to the function. Only
	parts that show differences are presented here.)
	
	Interface Differences between FPS NT and Fortran 5.1
	----------------------------------------------------
	1) FPS NT  INTEGER*4 FUNCTION FOCUSQQ(INTEGER*4 IUNIT)
	  F5.1    INTEGER*2 FUNCTION FOCUSQQ(INTEGER*2 IUNIT)
	
	2) FPS NT  INTEGER*4 FUNCTION INQFOCUSQQ(INTEGER*4 IUNIT)
	  F5.1    INTEGER*2 FUNCTION INQFOCUSQQ(INTEGER*2 IUNIT)
	
	3) FPS NT  INTEGER*4 FUNCTION ABOUTBOXQQ(CHARACTER*(*)STR)
	  F5.1    INTEGER*2 FUNCTION ABOUTBOXQQ(CHARACTER*(*)STR)
	
	4) FPS NT  INTEGER*4 FUNCTION CLICKQQ(INTEGER*4 ITEM)
	  F5.1    INTEGER*2 FUNCTION CLICKQQ(INTEGER*2 ITEM)
	
	5) FPS NT  INTEGER*4 FUNCTION SETWSIZEQQ(INTEGER*4 IUNIT, WINFO)
	  F5.1    INTEGER*2 FUNCTION SETWSIZEQQ(INTEGER*2 IUNIT, WINFO)
	
	6) FPS NT  INTEGER*4 GETWSIZEQQ(INTEGER*4 IUNIT,INTEGER*4 IREQ,WINFO)
	  F5.1    INTEGER*2 GETWSIZEQQ(INTEGER*2 IUNIT,INTEGER*2 IREQ,WINFO)
	
	7) FPS NT  INTEGER*4 FUNCTION MESSAGEBOXQQ(MSG,CAPTION, INTEGER*4 MTYPE)
	  F5.1    INTEGER*2 FUNCTION MESSAGEBOXQQ(MSG,CAPTION, INTEGER*2 MTYPE)
	
	8) FPS NT  INTEGER*4 FUNCTION WGSETACTIVEQQ(handle)
	          INTEGER*4 handle
	  F5.1    INTEGER*2 FUNCTION WGSETACTIVEQQ(handle)
	          INTEGER*2 handle
	
	9) FPS NT  INTEGER*4 FUNCTION WGGETACTIVEQQ()
	  F5.1    INTEGER*2 FUNCTION WGGETACTIVEQQ()
	
	Starting from the MS-DOS Command Line  (page 114 in 5.1 Advanced Topics)
	-------------------------------------
	Run QuickWin programs from the Windows NT command prompt simply by typing
	the application's name.  Doing so will launch the application and switch
	to graphics mode if necessary.  Unless you use the Windows NT START
	command, that command prompt will not be accessible until after the
	application terminates.
	
	QuickWin Windows  (page 118 in 5.1 Advanced Topics)
	----------------
	Window contents are now copied to the Clipboard only as bitmaps
	(graphics);  text windows are no longer supported.
	
	READ statements no longer cause windows to scroll down.
	
	The default color for text is now white on black.
	
	The QuickWin Menus  (page 119-21 in 5.1 Advanced Topics)
	------------------
	The View menu is new for NT. This menu provides scaling options.
	
	The File menu includes two new options: Print and Save.
	
	Since text windows no longer exist, the Edit menu now includes just
	Copy and Paste.
	
	Marking is no longer necessary since copying always takes the entire
	drawing area.
	
	The State menu has combined the Pause and Resume commands into a single
	option, which simply toggles the program's execution state. The label
	of this option changes as appropriate.
	
	To conform to Windows programming conventions, the Index option in the
	Help menu has been renamed "Contents."
	
	QuickWin Enhancements  (page 122 in 5.1 Advanced Topics)
	---------------------
	The FILE=" " parameter for the OPEN statement now brings up the
	standard Windows File Open dialog box.
	
	There are new menu functions for appending, deleting, and renaming menu
	items. See the FORTRAN Language Help file for additional details.
	
	Graphics Library Routines  (page 179 in 5.1 Advanced Topics)
	-------------------------
	OS/2 support is no longer provided.
	
	QuickWin now supports all graphics cards supported by Windows NT. EGA
	and CGA are no longer supported.
	
	Selecting Display Options  (page 181 in 5.1 Advanced Topics)
	-------------------------
	SETVIDEOMODE, SETVIDEOMODEROWS, SETVISUALPAGE, GETVISUALPAGE,
	SETATIVEPAGE, and GETACTIVEPAGE are now obsolete.  These routines
	are provided for backward compatibility, but the newer alternate
	APIs should be used in new code.
	
	DISPLAYCURSOR settings are reset by a call to SETWINDOWCONFIG to
	$GCURSOROFF.
	
	General topics
	--------------
	The YIELDQQ function, which was required under Win16 to allow the
	application to cooperate in multitasking, is still useful, even though
	Windows NT is a fully preemptive multitasking operating system.  The
	application must yield at some point to allow the application to
	respond to its own menus, including the system menu.  The compiler
	still inserts YIELDQQ statements into the generated object code when
	an application is compiled with /MW unless the option is changed to
	/MW0.  You can insert additional calls to YIELDQQ in loops where you
	might want to interact with menus and windows.
	
	Callback functions used for menu items must be declared to accept a
	LOGICAL*4 argument even though the function does not intend to use
	menu checkmarks.  If you fail to declare the function correctly, a
	memory access violation will occur when you select the menu item
	calling that callback function.
	
	Additional query words: 1.00
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbFortranSearch kbZNotKeyword2 kbFORTRANPower32100NT
	Version           : :1.0
	
	=============================================================================
	

{% endraw %}
