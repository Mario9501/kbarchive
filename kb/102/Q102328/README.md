---
layout: page
title: "Q102328: HOWTO: Center a Dialog Using the Microsoft Foundation Classes"
permalink: /kb/102/Q102328/
---

## Q102328: HOWTO: Center a Dialog Using the Microsoft Foundation Classes

{% raw %}

	Article: Q102328
	Product(s): Microsoft C Compiler
	Version(s): 1.0,1.5,1.51,1.52,2.0,2.1,4.0,7.0
	Operating System(s): 
	Keyword(s): kbDlg kbMFC KbUIDesign kbVC100 kbVC150 kbVC200 kbVC400 kbVC500 kbVC600 kbGrpDSMFCATL
	Last Modified: 26-MAR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), used with:
	   - Microsoft C/C++ for MS-DOS, version 7.0 
	   - Microsoft Visual C++ for Windows, 16-bit edition, versions 1.0, 1.5, 1.51, 1.52 
	   - Microsoft Visual C++, 32-bit Editions, versions 1.0, 2.0, 2.1, 4.0 
	   - Microsoft Visual C++.NET (2002) 
	-------------------------------------------------------------------------------
	
	NOTE: Microsoft Visual C++ NET (2002) supported both the managed code model that is provided by the .NET Framework and the unmanaged native Windows code model. The information in this article applies to unmanaged Visual C++ code only.
	
	SUMMARY
	=======
	
	In an application developed with the Microsoft Foundation Classes library, you
	may want to automatically center a dialog box with respect to its parent window
	when it is created.
	
	To do this, it is necessary to ensure that the dialog box can be centered without
	regard to its parent window (to support the case in which the caller specified
	NULL as the parent window handle). You must add additional code to center the
	dialog box with respect to the desktop window when no parent is specified and
	with respect to the parent window otherwise.
	
	MORE INFORMATION
	================
	
	The sample code below can be used as an example to override the OnInitDialog()
	member function of the CDialog class. The CenterDialog() function, defined
	below, is compatible with version 1.0 of the Microsoft Foundation Classes
	library.
	
	If you develop your application with version 2.0 or later of the Microsoft
	Foundation Classes library, use the CenterWindow() function instead of the
	CenterDialog() function. CenterWindow() provides identical functionality, but it
	is not available in version 1.0 of the MFC library.
	
	The MFC version 2.0 implementation of the CenterWindow() function can be found in
	the DLGCORE.CPP file (installed by default in the C:\MFC\SRC directory). In MFC
	version 3.0 and above, CenterWindow() is a member function of CWnd which is the
	base class of CDialog. In these MFC versions, the implementation of
	CWnd::CenterWindow() can be found in WINCORE.CPP (installed by default in the
	MFC\SRC subdirectory of the corresponding Visual C++ product directory).
	
	Sample Code
	-----------
	
	     /*
	      * Compiler options needed: (Standard Windows Requirements)
	      */ 
	
	     void CMyDialog::CenterDialog(CWnd *MyDialogPtr)
	     {
	        CPoint   Point;
	        CRect    DialogRect;
	        CRect    ParentRect;
	        int      nWidth;
	        int      nHeight;
	        CWnd     *DesktopWindow = NULL;
	        CWnd     *MainWindow;
	
	        // Get the size of the dialog box.
	        MyDialogPtr->GetWindowRect(DialogRect);
	
	        // Get the main window.
	        MainWindow = AfxGetApp()->m_pMainWnd;
	
	        // Determine if the main window exists. This can be useful when
	        // the application creates the dialog box before it creates the
	        // main window. If it does exist, retrieve its size to center
	        // the dialog box with respect to the main window.
	        if (MainWindow != NULL)
	           MainWindow->GetClientRect(ParentRect);
	        // If the main window does not exist, center with respect to
	        // the desktop window.
	        else
	        {
	           DesktopWindow = MyDialogPtr->GetDesktopWindow();
	           DesktopWindow->GetWindowRect(ParentRect);
	        }
	
	        // Calculate the height and width for MoveWindow().
	        nWidth = DialogRect.Width();
	        nHeight = DialogRect.Height();
	
	        // Find the center point and convert to screen coordinates.
	        Point.x = ParentRect.Width() / 2;
	        Point.y = ParentRect.Height() / 2;
	        if (MainWindow)
	           MainWindow->ClientToScreen(&Point);
	        else
	           DesktopWindow->ClientToScreen(&Point);
	
	        // Calculate the new X, Y starting point.
	        Point.x -= nWidth / 2;
	        Point.y -= nHeight / 2;
	
	        // Move the window.
	        MyDialogPtr->MoveWindow(Point.x, Point.y, nWidth, nHeight, FALSE);
	     }
	
	     BOOL CMyDialog::OnInitDialog()
	     {
	        CDialog::OnInitDialog();
	
	        // Remove the comment from 1 or 2 below to correspond with
	        // the version of the Microsoft Foundation Classes library
	        // you are using.
	
	        // 1. Call CenterDialog() for version 1.0
	        // CenterDialog(this);
	
	        // 2. Call CenterWindow() for versions 2.0 and above
	        // CenterWindow();
	
	        return TRUE;
	     }
	
	Additional query words: kbDlg
	
	======================================================================
	Keywords          : kbDlg kbMFC KbUIDesign kbVC100 kbVC150 kbVC200 kbVC400 kbVC500 kbVC600 kbGrpDSMFCATL 
	Technology        : kbAudDeveloper kbMFC
	Version           : :1.0,1.5,1.51,1.52,2.0,2.1,4.0,7.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
