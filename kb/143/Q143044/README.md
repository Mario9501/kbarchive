---
layout: page
title: "Q143044: INFO: How Visual Basic 4.0 Handles Files Marked Read-Only"
permalink: /kb/143/Q143044/
---

## Q143044: INFO: How Visual Basic 4.0 Handles Files Marked Read-Only

{% raw %}

	Article: Q143044
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:4.0;
	Operating System(s): 
	Keyword(s): kbenv kbVBp400 kbGrpDSVB
	Last Modified: 04-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual SourceSafe, 16-bit, for Windows, version 4.0 
	- Microsoft Visual SourceSafe, 32-bit, for Windows 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Visual Basic 4.0 may handle files with the read-only attribute set differently
	than Visual Basic 3.0. This may result in a "Can't Edit Module" error when
	trying to change a code module. The Visual Basic 4.0 development environment
	will handle read-only files in one of two ways. The way Visual Basic 4.0 behaves
	is dependent on the current setting of the ReadOnlyMode property of the
	development environment. If the ReadOnlyMode is set to 0 (lenient) you will be
	able to edit files marked read-only just like Visual Basic 3.0. Of course you
	will still not be able to save your changes. If the ReadOnlyMode is set to 1
	(strict) Visual Basic will not allow you to edit files marked read-only.
	
	MORE INFORMATION
	================
	
	The default ReadOnlyMode for Visual Basic 4.0 is lenient. However, the default
	can be changed to strict by adding ReadOnlyMode=1 to the Visual Basic section of
	the VB.INI.
	
	ReadOnlyMode can also be changed dynamically by Visual Basic 4.0 add-ins through
	the ReadOnlyMode property of the Application object of Visual Basic 4.0 add-in
	object model. The Microsoft SourceSafe add-in for Visual Basic 4.0 sets Visual
	Basic 4.0 to the strict mode. The following example shows you how to create a
	add-in that will allow you to toggle the ReadOnlyMode from a menu item.
	
	Example
	-------
	
	1. Start a new project.
	
	2. Remove the default Form1.
	
	3. Add a reference to "Microsoft Visual Basic 4.0 Development Environment" using
	  the Tools/References dialog.
	
	4. Add a new standard module (Module1.BAS by default).
	
	5. Put the following code in the standard module:
	
	        ''' MODULE1.BAS
	        '''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
	        #If Win16 Then
	           Declare Function WritePrivateProfileString Lib "KERNEL" ( _
	              ByVal AppName As String, ByVal KeyName As String, _
	              ByVal keydefault As String, ByVal FileName As String) As _
	              Integer
	           Declare Function GetPrivateProfileString Lib "KERNEL" ( _
	              ByVal AppName As String, ByVal KeyName As String, _
	              ByVal keydefault As String, ByVal ReturnString As String, _
	              ByVal NumBytes As Integer, ByVal FileName As String) As Integer
	        #ElseIf Win32 Then
	           Declare Function WritePrivateProfileString Lib "KERNEL32" _
	              Alias "WritePrivateProfileStringA" (ByVal AppName As String, _
	              ByVal KeyName As String, ByVal keydefault As String, _
	              ByVal FileName As String) As Long
	           Declare Function GetPrivateProfileString Lib "KERNEL32" _
	              Alias "GetPrivateProfileStringA" (ByVal AppName As String, _
	              ByVal KeyName As String, ByVal keydefault As String, _
	              ByVal ReturnString As String, ByVal NumBytes As Long, _
	              ByVal FileName As String) As Long
	        #End If
	
	        Sub Main()
	           #If Win16 Then
	              Const Section = "Add-Ins16"
	           #ElseIf Win32 Then
	              Const Section = "Add-Ins32"
	           #End If
	           Const BufSize = 255
	
	           Dim Ret As Variant
	           Dim RetStr As String
	
	           ' Check to see if the entry is already in the VB.INI file.
	           ' Add if not.
	
	           RetStr = Space(BufSize)
	           Ret = GetPrivateProfileString(Section, "ReadOnlyMode.Switch", _
	              "NotFound", RetStr, BufSize, "VB.INI")
	           RetStr = Left(RetStr, Ret)
	           If RetStr = "NotFound" Then
	              WritePrivateProfileString Section, "ReadOnlyMode.Switch", _
	                 "0", "VB.INI"
	           End If
	        End Sub
	
	        ''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
	
	6. Add a new class module to the project (Class1.CLS by default.)
	
	7. Set the following properties of the class module to the specified values:
	
	     Property        Value
	     ---------------------------------------
	
	     Instancing      1 - Creatable MultiUse
	     Name            Switch
	     Public          True
	
	8. Put the following code in the class module:
	
	        ''' CLASS1.CLS
	        ''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
	        Option Explicit
	
	        Private ThisInstance As VBIDE.Application
	        Private AddInMenuLine As VBIDE.MenuLine
	        Private AddInID As Long
	
	        Public Sub ConnectAddIn(VBInstance As Object)
	           Set ThisInstance = VBInstance
	           Set AddInMenuLine = ThisInstance.AddInMenu.MenuItems.Add( _
	              "Strict &ReadOnlyMode")
	           AddInMenuLine.Checked = ThisInstance.ReadOnlyMode
	           AddInID = AddInMenuLine.ConnectEvents(Me)
	        End Sub
	
	        Public Sub DisconnectAddIn(Mode As Integer)
	           AddInMenuLine.DisconnectEvents AddInID
	           ThisInstance.AddInMenu.MenuItems.Remove AddInMenuLine
	        End Sub
	
	        Public Sub AfterClick()
	           ThisInstance.ReadOnlyMode = ThisInstance.ReadOnlyMode Xor 1
	           AddInMenuLine.Checked = ThisInstance.ReadOnlyMode
	        End Sub
	
	        ''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
	
	9. Set the following Project Options:
	
	     Option            Value
	     ----------------------------------------
	
	     Startup Form      Sub Main
	     Project Name      ReadOnlyMode
	     StartMode         OLE Server
	     Error Trapping    Break in Class Module
	
	10. Save the project.
	
	11. Run the project.
	
	12. Start up a second instance of Visual Basic (Form1 is created by default.)
	
	13. Use the Add-In Manager to add the ReadOnlyMode.Switch add-in.
	
	14. Open a code module with that has the read-only attribute set. You can tell
	  if a file is marked read-only by the small red lock that appears in the
	  project window next to the file.
	
	15. From the Add-In menu you can switch the ReadOnlyMode. When checked the
	  environment will be in strict mode and when unchecked it will be in lenient
	  mode.
	
	Additional query words: Addin Addins VBIDE ssafe
	
	======================================================================
	Keywords          : kbenv kbVBp400 kbGrpDSVB 
	Technology        : kbVBSearch kbSSafeSearch kbAudDeveloper kbVB400Search kbVB400 kbVB16bitSearch kbSSafe400 kbSSafe16bitSearch kbSSafe32bitSearch
	Version           : WINDOWS:4.0;
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
