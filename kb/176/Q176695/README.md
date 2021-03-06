---
layout: page
title: "Q176695: PRB: ExitWindowsEx API Does Not Reboot Windows NT"
permalink: /kb/176/Q176695/
---

## Q176695: PRB: ExitWindowsEx API Does Not Reboot Windows NT

{% raw %}

	Article: Q176695
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:4.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kbVBp400 kbVBp500 kbVBp600 kbGrpDSVB kb32bitOnly
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you use the ExitWindowsEx API to reboot the system under Windows NT and
	Windows 2000, the machine does not reboot.
	
	CAUSE
	=====
	
	In order to programmatically reboot a Windows NT or Windows 2000 system, the
	process requires the SE_SHUTDOWN_NAME privilege. By default, Visual Basic
	applications do not have this privilege and therefore will not reboot the
	machine.
	
	RESOLUTION
	==========
	
	In order to get ExitWindowsEx API to reboot the system under Windows NT or
	Windows 2000, the SE_SHUTDOWN_NAME privilege must be set. The following steps
	describe how to get the ExitWindowsEx API to work under Windows NT and Windows
	2000.
	
	Step By Step Example
	--------------------
	
	1. Create a new standard EXE in Visual Basic. Form1 is created by default.
	
	2. View the code for Form1. In the Declarations section, add the following code:
	
	        Private Type LUID
	           UsedPart As Long
	           IgnoredForNowHigh32BitPart As Long
	        End Type
	
	        Private Type TOKEN_PRIVILEGES
	          PrivilegeCount As Long
	          TheLuid As LUID
	          Attributes As Long
	        End Type
	
	        Private Const EWX_SHUTDOWN As Long = 1
	        Private Const EWX_FORCE As Long = 4
	        Private Const EWX_REBOOT = 2
	
	        Private Declare Function ExitWindowsEx Lib "user32" (ByVal _
	             dwOptions As Long, ByVal dwReserved As Long) As Long
	
	        Private Declare Function GetCurrentProcess Lib "kernel32" () As Long
	        Private Declare Function OpenProcessToken Lib "advapi32" (ByVal _
	           ProcessHandle As Long, _
	           ByVal DesiredAccess As Long, TokenHandle As Long) As Long
	        Private Declare Function LookupPrivilegeValue Lib "advapi32" _
	           Alias "LookupPrivilegeValueA" _
	           (ByVal lpSystemName As String, ByVal lpName As String, lpLuid _
	           As LUID) As Long
	        Private Declare Function AdjustTokenPrivileges Lib "advapi32" _
	           (ByVal TokenHandle As Long, _
	           ByVal DisableAllPrivileges As Long, NewState As TOKEN_PRIVILEGES _
	           , ByVal BufferLength As Long, _
	        PreviousState As TOKEN_PRIVILEGES, ReturnLength As Long) As Long
	
	3. Add a procedure called AdjustToken with the following code:
	
	        Private Sub AdjustToken()
	           Const TOKEN_ADJUST_PRIVILEGES = &H20
	           Const TOKEN_QUERY = &H8
	           Const SE_PRIVILEGE_ENABLED = &H2
	           Dim hdlProcessHandle As Long
	           Dim hdlTokenHandle As Long
	           Dim tmpLuid As LUID
	           Dim tkp As TOKEN_PRIVILEGES
	           Dim tkpNewButIgnored As TOKEN_PRIVILEGES
	           Dim lBufferNeeded As Long
	
	           hdlProcessHandle = GetCurrentProcess()
	           OpenProcessToken hdlProcessHandle, (TOKEN_ADJUST_PRIVILEGES Or _
	              TOKEN_QUERY), hdlTokenHandle
	
	        ' Get the LUID for shutdown privilege.
	           LookupPrivilegeValue "", "SeShutdownPrivilege", tmpLuid
	
	           tkp.PrivilegeCount = 1    ' One privilege to set
	           tkp.TheLuid = tmpLuid
	           tkp.Attributes = SE_PRIVILEGE_ENABLED
	
	       ' Enable the shutdown privilege in the access token of this process.
	           AdjustTokenPrivileges hdlTokenHandle, False, _
	           tkp, Len(tkpNewButIgnored), tkpNewButIgnored, lBufferNeeded
	
	       End Sub
	
	4. Add a CommandButton to the form. In the Click event, add the following code:
	
	        Private Sub Command1_Click()
	           AdjustToken
	           ExitWindowsEx (EWX_SHUTDOWN Or EWX_FORCE Or EWX_REBOOT), &HFFFF
	        End Sub
	
	5. Save the project and build an executable. When you run the executable and
	  click the CommandButton the computer will reboot as expected.
	
	STATUS
	======
	
	This behavior is by design.
	
	REFERENCES
	==========
	
	For additional information, please see the following articles in the Microsoft
	Knowledge Base:
	
	  Q142820 HOWTO: Terminate Windows from a 16-Bit VB Application
	
	  Q76981 VB3: HOWTO: Terminate Windows from a Visual Basic Application
	
	  Q168796 HOWTO: Programmatically Restart or Log Off a Computer
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbVBp400 kbVBp500 kbVBp600 kbGrpDSVB kb32bitOnly 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500 kbVBA600 kbVB500 kbVB600 kbVB400Search kbVB400
	Version           : WINDOWS:4.0,5.0,6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
