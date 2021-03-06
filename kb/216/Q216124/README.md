---
layout: page
title: "Q216124: BUG: Reinstalling App Fails To Replace Text File With Same Date"
permalink: /kb/216/Q216124/
---

## Q216124: BUG: Reinstalling App Fails To Replace Text File With Same Date

{% raw %}

	Article: Q216124
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kberrmsg kbVBp600bug kbGrpDSVB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If you install a Visual Basic 6.0 application that includes a text file (or any
	file that does not have a version number) in the distribution set, and reinstall
	the application without removing it first, the following warning message is
	displayed:
	
	  A file being copied is older than the file currently on your system. It is
	  recommended that you keep your existing file.
	
	CAUSE
	=====
	
	The Visual Basic 6.0 application setup program incorrectly assumes that the text
	file on the system is newer than the one in the distribution set, even though
	the files have the exact same date.
	
	RESOLUTION
	==========
	
	The warning message is caused by the following statement in the CopySection Sub
	in the basSetup1 module of the Setup Toolkit project (Setup1.vbp):
	
	  If sFile.varDate <= FileDateTime(strDestDir & strDestName) Then
	
	Because text files do not have version numbers, the dates are being compared. For
	the file to be installed, setup checks the date of that file in Setup.lst and
	sees if it is less than (<) or equal to (=) the date of the destination file
	(that is being overwritten in this case). If this statement is TRUE, it warns
	the user that the file being copied is older than the file on the system. As can
	be seen, the equal sign (=) causes the problem. If we change the "<=" to just
	"<" as in the following code segment, the error message will not be shown:
	
	  If sFile.varDate < FileDateTime(strDestDir & strDestName) Then
	
	NOTE: You will need to recompile the Setup1.exe file after making the
	modification to the Setup Toolkit project (Setup1.vbp), and then you need to
	re-run the Project and Deployment Wizard (PDW) to recreate the application setup
	files.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a new Standard EXE project in Visual Basic. Form1 is created by
	  default.
	
	2. Select Make Project1.exe from the File menu to compile the project.
	
	3. Use Notepad to create a text file called test1.txt.
	
	4. Click the Start button, and then point to Programs. Select Microsoft Visual
	  Basic 6.0, and choose Package and Deployment Wizard from Microsoft Visual
	  Basic 6.0 Tools.
	
	5. Browse to Project1 and select Package to build the distribution set for the
	  project.
	
	6. In the "Included File" screen, click Add to activate the Add Files dialog.
	  Browse to test1.txt and add it to the set. Click Next for the following
	  screens to finish building the set.
	
	7. Install the distribution set onto a target computer twice, without removing
	  the application between installations. The above error message will be
	  displayed the second time the setup program is run.
	
	REFERENCES
	==========
	
	For more information, please search the MSDN Library included within Visual
	Studio 6.0 on the phrase "Setup Toolkit" for features of the wizard.
	
	Additional query words:
	
	======================================================================
	Keywords          : kberrmsg kbVBp600bug kbGrpDSVB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVBA600 kbVB600
	Version           : WINDOWS:6.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
