---
layout: page
title: "Q258965: PRB: ImgEdit.OCX Causes Breakpoint in RtlFreeHeap w/ VC Debugger"
permalink: /kb/258/Q258965/
---

## Q258965: PRB: ImgEdit.OCX Causes Breakpoint in RtlFreeHeap w/ VC Debugger

{% raw %}

	Article: Q258965
	Product(s): Microsoft C Compiler
	Version(s): 4.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kbActiveX kbCOMt kbCtrl kbInprocSvr kbMFC kbGrpDSMFCATL
	Last Modified: 14-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, 32-bit Enterprise Edition, versions 5.0, 6.0 
	- Microsoft Visual C++, 32-bit Professional Edition, versions 5.0, 6.0 
	- Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	- Microsoft Visual C++.NET (2002) 
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you use the ImgEdit.ocx control in a MFC application running on Windows NT
	4.0, you may get a debug assertion in the RtlHeapFree function when you exit a
	debug build of the application. However, when you employ the same control in
	Visual Basic, you do not encounter the debug assertion in RtlHeapFree upon
	exiting. In addition, when you use the ImgEdit.ocx control in a release build of
	a MFC application on Windows NT 4.0, the control does not reveal this assertion.
	And the assertion does not appear when you you run the application on Windows
	95, Windows 98 or Windows 2000, but appears does appear on Windows NT 4.0.
	
	CAUSE
	=====
	
	This is a bug in the ImgEdit.ocx control. The assertion can be safely ignored
	because it is only given one time and that is when the application is shutting
	down. This assertion does not cause any problems when you are running in release
	builds.
	
	RESOLUTION
	==========
	
	Ignore the assertion as it is harmless in this case.
	
	
	STATUS
	======
	
	This behavior is a bug in the ImgEdit.ocx control.
	
	NOTE: The third-party products that are discussed in this article are
	manufactured by companies that are independent of Microsoft. Microsoft makes no
	warranty, implied or otherwise, regarding the performance or reliability of
	these products.
	
	Additional query words: Wang Image Edit Control
	
	======================================================================
	Keywords          : kbActiveX kbCOMt kbCtrl kbInprocSvr kbMFC kbGrpDSMFCATL 
	Technology        : kbVCsearch kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbAudDeveloper kbVC500 kbVC600 kbVC32bitSearch kbVCNET kbVC500Search
	Version           : :4.0,5.0,6.0
	Issue type        : kbprb
	Solution Type     : kbnofix
	
	=============================================================================
	

{% endraw %}
