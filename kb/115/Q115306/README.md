---
layout: page
title: "Q115306: HOWTO: How to Get the Current State of a Button in a CToolbar"
permalink: /kb/115/Q115306/
---

## Q115306: HOWTO: How to Get the Current State of a Button in a CToolbar

{% raw %}

	Article: Q115306
	Product(s): Microsoft C Compiler
	Version(s): winnt:2.0,2.1,4.0
	Operating System(s): 
	Keyword(s): kbMFC kbToolbar KbUIDesign kbVC kbVC100 kbVC200 kbVC400 kbGrpDSMFCATL
	Last Modified: 07-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), used with:
	   - Microsoft Visual C++ for Windows, 16-bit edition, versions 1.0, 1.5, 1.51, 1.52 
	   - Microsoft Visual C++, 32-bit Editions, versions 2.0, 2.1, 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Although the Microsoft Foundation Classes (MFC) offer a useful and easy method
	of keeping the state of a menu command and/or toolbar button in a CControlBar
	tied together, there is no easy means of finding out the command's or button's
	current state.
	
	MORE INFORMATION
	================
	
	To find the current state of a menu command or toolbar button in a
	CControlBar-derived class, use the following piece of code:
	
	        UINT iButtonID;
	        UINT iButtonStyle;
	        int iButtonImage;
	
	        // If the Toolbar is not based upon the default "AFX_IDW_TOOLBAR"
	        // constant, then replace its use with the valid Toolbar constant.
	
	        // If the following line is used from the Frame Window remove
	        //"GetParentFrame()->":
	        CToolBar* pBar =
	        (CToolBar*)GetParentFrame()->GetDescendantWindow(AFX_IDW_TOOLBAR);
	
	        // If this code sample is called from an AppWizard generated,
	        // Frame Window member function in Visual C++ 4.0, replace the above
	        // statement with the following. Recall that the CMDIFrameWnd-derived
	        // Frame Window generated by AppWizard has a CToolBar m_wndToolBar
	        // member.
	        CToolBar* pBar = &m_wndToolBar;
	
	        if (pBar != NULL) {
	
	             // Use the relevant Button ID for the following line:
	             int iButtonIndex = pBar->CommandToIndex(ID_MY_BUTTON);
	
	             pBar->GetButtonInfo(iButtonIndex, iButtonID, iButtonStyle,
	        iButtonImage);
	
	             // The following code checks for all possible states.
	             // In practice, check only for those states that you need.
	
	             if (iButtonStyle & TBBS_PRESSED)
	                  // Button Down
	             else
	                  if (iButtonStyle & (TBBS_CHECKED & TBBS_DISABLED))
	                       // Button Down & Unavailable
	                  else
	                       if (iButtonStyle & TBBS_DISABLED)
	                            // Button Disabled
	                       else
	                            if (iButtonStyle & TBBS_INDETERMINATE)
	                                 // Button State Indeterminate
	                            else
	                                 if (iButtonStyle & TBBS_CHECKED)
	                                      // Button Checked
	                                 else
	                                      // Button Up & Enabled
	
	        }
	
	Additional query words: 1.00 1.50 2.00 2.10 2.50 2.51 2.52 3.00 3.10 4.00 kbinf kbVC1500
	
	======================================================================
	Keywords          : kbMFC kbToolbar KbUIDesign kbVC kbVC100 kbVC200 kbVC400 kbGrpDSMFCATL 
	Technology        : kbAudDeveloper kbMFC
	Version           : winnt:2.0,2.1,4.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
