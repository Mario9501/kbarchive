---
layout: page
title: "Q257688: FIX: Printer Object Fails to Track Default Printer"
permalink: /kb/257/Q257688/
---

## Q257688: FIX: Printer Object Fails to Track Default Printer

{% raw %}

	Article: Q257688
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 6.0
	Operating System(s): 
	Keyword(s): kbprint kbAPI kbCmnDlgPrint kbPrinting kbSDKWin32 kbVBp600bug kbGrpDSVB kbDSupport
	Last Modified: 11-SEP-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you try to select a printer in the Printer dialog box and then change a
	property of the Printer object, such as orientation, the Printer object does not
	retain the selected default printer setting.
	
	RESOLUTION
	==========
	
	You can work around this problem by following either one of the two methods
	outlined here:
	
	Workaround #1 (for Windows 95, Windows 98, and Windows Me systems only)
	
	Use the GetProfileString function to obtain the default printer information.
	
	On Windows 9x and Windows Me systems, the default printer setting is stored in
	the Registry and in the [Windows] section of the win.ini file in the windows
	folder. The code line starting with "Device=" shows information about the
	default printer. The [Devices] section has information about all installed
	printers in the system.
	
	On Microsoft Windows NT and Microsoft Windows 2000, this information is stored in
	the Registry. The GetPrifileString function retrieves the default printer
	information on any of these systems because the win.ini file entries are
	remapped to the Registry. However, selecting a printer from the Common dialog
	box under Windows NT and Windows 2000 does not make it the default printer. See
	the "References" section of this article for more information.
	
	Workaround #2
	
	Set Printer.TrackDefault=True after changing the printer in the Printer dialog
	box as follows:
	
	  Private Sub Command1_Click()
	      CommonDialog1.ShowPrinter
	      Printer.TrackDefault=True 
	      MsgBox Printer.DeviceName
	  End Sub
	
	STATUS
	======
	
	Microsoft has confirmed that this is a bug in the Microsoft products that are
	listed at the beginning of this article. This bug was corrected in the latest
	service pack for Visual Studio 6.0.
	
	Microsoft has confirmed that this is a bug in the Microsoft products that are
	listed at the beginning of this article. This bug was corrected in the latest
	service pack for Visual Studio 6.0.
	
	For additional information about Visual Studio service packs, click the following
	article numbers to view the articles in the Microsoft Knowledge Base:
	
	  Q194022 INFO: Visual Studio 6.0 Service Packs, What, Where, Why
	
	  Q194295 HOWTO: Tell That a Visual Studio Service Pack Is Installed
	
	To download the latest Visual Studio service pack, visit the following Microsoft
	Web site:
	
	  http://msdn.microsoft.com/vstudio/downloads/updates.asp
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a new Standard EXE project in Visual Basic. Form1 is created by
	  default.
	
	2. From the Project menu, select Components, check Microsoft Common Dialog
	  Control 6.0, and then click OK.
	
	3. Add four Command buttons and a Common Dialog control to Form1.
	
	4. Paste the following code into Form1's code window:
	
	  Option Explicit
	      
	  Private Declare Function GetProfileString Lib "kernel32" Alias _
	    "GetProfileStringA" (ByVal lpAppName As String, _
	    ByVal lpKeyName As String, ByVal lpDefault As String, _
	    ByVal lpReturnedString As String, ByVal nSize As Long) As Long
	      
	      Private Sub Command1_Click()
	          CommonDialog1.ShowPrinter
	          MsgBox Printer.DeviceName
	      End Sub
	      
	      Private Sub Command2_Click()
	          Dim DeviceName As String
	          Dim s As String
	          Dim size As Long
	          Dim p As Printer
	          
	          CommonDialog1.ShowPrinter
	          
	          size = 255
	          s = Space(255)
	          size = GetProfileString("Windows", "Device", vbNullString, s, size)
	          DeviceName = Left(s, InStr(1, s, ",") - 1)
	          For Each p In Printers
	              If p.DeviceName = DeviceName Then
	                  Set Printer = p
	                  Exit For
	              End If
	          Next p
	          
	          MsgBox Printer.DeviceName
	      End Sub
	      
	      Private Sub Command3_Click()
	          Printer.Orientation = vbPRORLandscape
	          Printer.Print "x"
	          Printer.EndDoc
	      End Sub
	      
	      Private Sub Command4_Click()
	          CommonDialog1.ShowPrinter
	          Printer.TrackDefault = True
	          MsgBox Printer.DeviceName
	      End Sub
	
	      Private Sub Form_Load()
	          Command1.Caption = "Broken"
	          Command2.Caption = "Fixed (Win 9x)"
	          Command3.Caption = "Orientation"
	          Command4.Caption = "Fixed"
	      End Sub
	
	5. Run the project and use the buttons named Fixed and Broken to display the
	  Printer dialog box. Change the printer selection each time. Note that the
	  message box displays the name of the printer that was selected.
	
	6. Click the button named Orientation.
	
	  Try using the Fixed and Broken buttons again. Notice that the message box
	  displayed by the Broken button does not reflect the printer selected in the
	  Printer dialog box. The message box displayed by Fixed reflects the printer
	  selected in the Printer dialog box. On Windows 9x and Windows Me systems you
	  can also see that the Fixed (Win 9x/Me) button works.
	
	REFERENCES
	==========
	
	For additional information, click the article number below to view the article
	in the Microsoft Knowledge Base:
	
	  Q198712 PRB: CommonDialog Changes System Wide Printer Properties
	
	Additional query words:
	
	======================================================================
	Keywords          : kbprint kbAPI kbCmnDlgPrint kbPrinting kbSDKWin32 kbVBp600bug kbGrpDSVB kbDSupport 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVB600
	Version           : :6.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
