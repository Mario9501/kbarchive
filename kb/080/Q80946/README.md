---
layout: page
title: "Q80946: RoEdit.exe Implements Read-Only Edit Control in Windows"
permalink: /kb/080/Q80946/
---

## Q80946: RoEdit.exe Implements Read-Only Edit Control in Windows

{% raw %}

	Article: Q80946
	Product(s): Microsoft Windows Software Development Kit
	Version(s): WINDOWS:3.0,3.1
	Operating System(s): 
	Keyword(s): kbfile kbsample kb16bitonly kbCtrl kbEditCtrl kbGrpDSUser kbOSWin310
	Last Modified: 10-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows Software Development Kit (SDK) versions 3.0, 3.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	In some situations, an application may contain text that is displayed for the
	user to read, which is undesirable for the user to modify. The application can
	use a static control to contain this text if the message is short. However, for
	larger amounts of text, which require scrolling to display all the text in the
	allotted area, something closer to an edit control is required. This article,
	and its associated sample code, details how to make an edit control "read-
	only."
	
	MORE INFORMATION
	================
	
	The following files are available for download from the Microsoft Download
	Center:
	
	RoEdit.exe
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. Once posted, the file is housed on secure
	servers that prevent any unauthorized changes to the file.
	
	
	An application can create a read-only edit control by subclassing or
	superclassing a standard edit control. The subclass procedure filters out
	messages that change the contents of the edit control. The following code
	fragment demonstrates this process:
	
	     FARPROC gOldProc;
	     LONG FAR PASCAL ROEditProc(HWND hWnd, WORD msg,
	
	                                WORD wParam, LONG lParam)
	     {
	         switch (msg)
	         {
	             case WM_KEYUP:
	             case WM_KEYDOWN:
	             case WM_CHAR:
	             case WM_CUT:
	             case WM_COPY:
	             case WM_PASTE:
	             case WM_LBUTTONUP:
	             case WM_LBUTTONDOWN:
	             case WM_LBUTTONDBLCLK:
	                 return 1L;
	             case WM_GETDLGCODE:
	                 return 0L;
	         }
	         return CallWindowProc(gOldProc, hWnd, msg, wParam, lParam);
	     } //*** ROEditProc
	
	In the example above, the subclass procedure traps mouse clicks, keystrokes, and
	the cut, copy, and paste commands. It also traps the WM_GETDLGCODE message to
	prevent an edit control in a dialog box from receiving the input focus.
	
	The following example demonstrates superclassing an edit control to create a new
	ROEDIT-class control that behaves similar to a read-only edit control. A ROEDIT
	control implements the window procedure provided above. It also changes the
	cursor to an arrow instead of an I-beam, which provides an additional indication
	to the user that the contents of the control cannot be changed. Using an ROEDIT
	control eliminates the necessity of subclassing each control after it is
	created. When the application creates a control from the ROEDIT class, the
	read-only behavior is provided automatically.
	
	The following code demonstrates superclassing an edit control as described
	above:
	
	     FARPROC gOldProc;
	     BOOL RegisterROEdit(HANDLE hInstance)
	     {
	         WNDCLASS wc;
	         if (!GetClassInfo(NULL, "EDIT", &wc))
	             return FALSE;
	         gOldProc = (FARPROC)wc.lpfnWndProc;
	         wc.style        &= ~CS_GLOBALCLASS;
	         wc.lpfnWndProc   = ROEditProc;
	         wc.hInstance     = hInstance;
	         wc.hCursor       = LoadCursor(NULL, IDC_ARROW);
	         wc.lpszClassName = "ROEDIT";
	
	         return RegisterClass(&wc);
	     } //*** RegisterROEdit
	
	In Windows 3.1, there is a new style bit for the edit control (ES_READONLY) that
	removes the editing capabilities of the edit control, leaving only the viewing
	capabilities. This style is useful when the application shows the user a body of
	static text that the user reads and does not modify.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbfile kbsample kb16bitonly kbCtrl kbEditCtrl kbGrpDSUser kbOSWin310 
	Technology        : kbAudDeveloper kbWin3xSearch kbSDKSearch kbWinSDKSearch kbWinSDK300 kbWinSDK310
	Version           : WINDOWS:3.0,3.1
	
	=============================================================================
	

{% endraw %}
