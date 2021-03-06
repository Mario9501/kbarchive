---
layout: page
title: "Q246233: FIX: Nested UserControl DataSource Property Causes Crash"
permalink: /kb/246/Q246233/
---

## Q246233: FIX: Nested UserControl DataSource Property Causes Crash

{% raw %}

	Article: Q246233
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kbCtrlCreate kbVBp kbVBp600bug kbGrpDSVB kbDSupport kbVS600sp4fix kbVS600sp5fix
	Last Modified: 26-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Visual Basic generates an Access Violation error when you select the DataSource
	property of a TextBox control that is placed on a UserControl. This only happens
	if the UserControl has been placed on a second UserControl in the same project.
	On computers that do not have Visual Studio Service Pack 3 installed, you may
	not get the Access Violation error. However, the control disappears. If you have
	a Data control on the UserControl that contains the TextBox, you always get the
	crash.
	
	RESOLUTION
	==========
	
	To resolve this problem, install Visual Studio 6.0 Service Pack 4.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug was corrected in the latest service pack for
	Visual Studio 6.0.
	
	For additional information about Visual Studio service packs, click the article
	numbers below to view the articles in the Microsoft Knowledge Base:
	
	  Q194022 INFO: Visual Studio 6.0 Service Packs, What, Where, Why
	
	  Q194295 HOWTO: Tell That a Visual Studio Service Pack Is Installed
	
	You can download the latest Visual Studio service pack from the following
	Microsoft Web site:
	
	  Visual Studio Product Updates
	  (http://msdn.microsoft.com/vstudio/downloads/updates.asp)
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a new Standard EXE project in Visual Basic. Form1 is created by
	  default.
	
	2. From the Project menu, choose Add User Control to add a UserControl
	  (UserControl1) to the project.
	
	3. Place a TextBox and a Data control on UserControl1.
	
	  NOTE: The Access Violation also happens without the Data control on computers
	  that have Visual Studio Service Pack 3.
	
	4. Close UserControl1.
	
	5. Add a second UserControl (UserControl2) to the project.
	
	6. Place UserControl1 on UserControl2.
	
	7. Close UserControl2 and Form1.
	
	8. Open UserControl1.
	
	9. Select Text1 on UserControl1, and, in the Properties window, click on the
	  DataSource property. The control might disappear. If so, repeat the preceding
	  two steps and Visual Basic generates the Access Violation error.
	
	Additional query words: sp4
	
	======================================================================
	Keywords          : kbCtrlCreate kbVBp kbVBp600bug kbGrpDSVB kbDSupport kbVS600sp4fix kbVS600sp5fix 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVB600
	Version           : WINDOWS:6.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
