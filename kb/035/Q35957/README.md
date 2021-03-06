---
layout: page
title: "Q35957: INFO: Active Application, Active Window, Input Focus Definition"
permalink: /kb/035/Q35957/
---

## Q35957: INFO: Active Application, Active Window, Input Focus Definition

{% raw %}

	Article: Q35957
	Product(s): Microsoft Windows Software Development Kit
	Version(s): WINDOWS:3.0,3.1
	Operating System(s): 
	Keyword(s): kb16bitonly kbSDKPlatform kbGrpDSUser kbWndw
	Last Modified: 12-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows Software Development Kit (SDK) versions 3.0, 3.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Although the concepts of "input focus," "active application," and "active
	window" are very closely related, there are differences among them.
	
	1. The "input focus" determines which window receives keyboard input.
	
	2. The "active window" is the window that receives the user's attention. If it's
	  an overlapped window or a pop-up window with a caption bar, the caption bar
	  is highlighted. If it's a dialog window, the frame is highlighted. Either the
	  active window or one of its child windows has the focus.
	
	3. The "active application" is the application that created the window that has
	  the input focus.
	
	MORE INFORMATION
	================
	
	The following discussion contains detailed definitions of the terms "input
	focus," "active window," and "active application," as well as a demonstration of
	those differences that you can perform using Windows Write.
	
	The following definition is from the glossary of "Programmer's Guide to Windows,
	Second Edition," by David Durant, Geta Carlson, and Paul Yao, published by
	Sybex, page 647:
	
	  Active Application
	
	  The active application is the application that created the window that
	  currently has the keyboard input focus. Applications do not need to be the
	  active application in order to receive and process messages. Applications are
	  notified by message whenever they are gaining or losing the status of "the
	  active application." The user normally determines the active application, but
	  applications can override this decision.
	
	For more information on the active application, refer to the documentation for
	the WM_ACTIVATEAPP message in the "Microsoft Windows Software Development Kit
	(SDK) Reference, Volume 1."
	
	The following is also from "Programmer's Guide to Windows, Second Edition," page
	655:
	
	  Focus
	
	  Keyboard input is transferred to the application as messages. Since several
	  windows may be visible on the screen simultaneously, there must be a method
	  for determining which of these windows should receive the keyboard input
	  messages. In Windows, the window that has the focus is the window that will
	  receive the keyboard messages. Normally, the user controls which window has
	  the focus by use of the mouse, but applications can transfer the focus from
	  window to window themselves.
	
	For more information on focus, refer to the documentation for the WM_SETFOCUS and
	WM_KILLFOCUS messages and for the GetFocus, SetFocus, and EnableWindow functions
	in the "SDK Reference, Volume 1."
	
	The following is from the book Programming Windows, Second Edition by Charles
	Petzold, published by Microsoft Press, pages 89-90:
	
	  Focus, Focus, Who's Got the Focus?
	
	  The keyboard must be shared by all applications running under Windows. Some
	  applications may have more than one window, and the keyboard must be shared
	  by these windows within the same application. When a key on the keyboard is
	  pressed, only one window procedure can receive a message that the key has
	  been pressed. The window that receives this keyboard message is the window
	  with the "input focus."
	
	  The concept of input focus is closely related to the concept of "active
	  window." The window with the input focus is either the active window or a
	  child window of the active window. The active window is usually easy to
	  identify. If the active window has a caption bar, Windows highlights the
	  caption bar. If the active window has a dialog frame (a form most commonly
	  seen in dialog boxes) instead of a caption bar, Windows highlights the frame.
	  If the active window is an icon, Windows highlights the window's caption bar
	  text below the icon.
	
	  The most common child windows are controls such as push buttons, radio
	  buttons, check boxes, scroll bars, edit boxes, and list boxes that usually
	  appear in a dialog box. Child windows are never themselves active windows. If
	  a child window has the input focus, then the active window is its parent.
	  Child window controls indicate that they have the input focus generally by
	  using a flashing cursor or caret.
	
	  If the active window is an icon, then no window has the input focus. Windows
	  continues to send keyboard messages to the icon, but these messages are in a
	  different form from keyboard messages sent to active windows that are not
	  icons.
	
	  A window procedure can determine when it has the input focus by trapping
	  WM_SETFOCUS and WM_KILLFOCUS messages. WM_SETFOCUS indicates that the window
	  is receiving the input focus, and WM_KILLFOCUS signals that the window is
	  losing the input focus.
	
	Petzold also indicates that Windows sends keyboard messages to icons differently
	than it does to windows with the focus. This difference is noted in the
	following excerpt from the "Microsoft Windows Software Development Kit
	Reference, Volume 1," page 4-381:
	
	  If a window is active but doesn't have the focus (that is, no window has the
	  focus), any key pressed will produce the WM_SYSCHAR, WM_SYSKEYDOWN, or
	  WM_SYSKEYUP message.
	
	For more information on the active window, refer to the documentation for the
	WM_ACTIVATE message and for the GetActiveWindow and SetActiveWindow functions in
	the "Microsoft Windows Software Development Kit Reference, Volume 1."
	
	Demonstration of Differences Between
	
	Focus, Active Application, and Active Window
	--------------------------------------------
	
	The following is an experiment you can do that will clarify the differences among
	active application, active window, and input focus, and show you how the user
	can specify which attribute is assigned to which window:
	
	Open Windows Write and choose Find from the Find menu. You'll now have a pop-up
	window that is a child of Write. Arrange your screen so that the Write, Find,
	and Program Manager windows are all on the screen together.
	
	If you click in the Program Manager window, both the Write window's and the Find
	dialog window's caption bars will be set to the inactive color, and the Program
	Manager window's caption bar will be set to the active color. At this point,
	Program Manager is the active application; it is also the active window and has
	the input focus.
	
	Click in the Write window; it will become the active application, as well as the
	active window, and will get the input focus.
	
	Click in the Find window; although it is now the active window, it is not the
	active application (Write is) nor does it have the input focus: the focus is in
	the Find What box, which is an edit control window that is a child of the Find
	dialog window, which is itself a pop-up-style window that is a child of Write.
	(Note that in this discussion the term "child windows" is used in terms of
	parent-child relationships rather than the child window style WS_CHILD.)
	
	At this point, you can move the input focus from box to box within the Find
	dialog window by using the TAB key (or by clicking with the mouse). There are
	three or four controls you can move between: Find What, Whole Word, Match
	Upper/Lowercase, and Find Next (available only if there is some text in the Find
	What box).
	
	Now press ALT+F6. This will make Write the active window instead of Find, and the
	focus will be set to the Write window as well; this is indicated by the flashing
	vertical caret. Press ALT+F6 a second time. Find will be the active window
	again, and the input focus will be set to whichever control it was last set to
	(Find What, Whole Word, Match Upper/Lowercase, or Find Next).
	
	Finally, you can use ALT+TAB to return to the Program Manager, making it the
	active application, the active window, and the one with the input focus. If you
	press ALT+TAB again, you will make Write the active application, Find the active
	window, and set the input focus to one of Find's controls (whichever one last
	had the focus).
	
	Additional query words:
	
	======================================================================
	Keywords          : kb16bitonly kbSDKPlatform kbGrpDSUser kbWndw 
	Technology        : kbAudDeveloper kbWin3xSearch kbSDKSearch kbWinSDKSearch kbWinSDK300 kbWinSDK310
	Version           : WINDOWS:3.0,3.1
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
