---
layout: page
title: "Q172578: HOWTO: Change the SQL Password Using RDO"
permalink: /kb/172/Q172578/
---

## Q172578: HOWTO: Change the SQL Password Using RDO

{% raw %}

	Article: Q172578
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 
	Operating System(s): 
	Keyword(s): kbGrpDSVBDB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The following is an example of how to change the SQL server password from Visual
	Basic using RDO and SQL Server's Stored Procedure - sp_Password. The article
	also gives examples of allowing users to change their passwords and allowing the
	SQL administrator to change the user's password.
	
	MORE INFORMATION
	================
	
	Step-by-Step Example
	--------------------
	
	1. In a new project add two CommandButton to the form.
	
	2. Copy the code in step 4 into the Form's Declaration section.
	
	3. Change the values for the password/username variables.
	
	4. Change the connection properties to match your connection. Note that this
	  example uses a DSN-less connection:
	
	     Private Sub Form_Load()
	       Command1.Caption = "User"
	       Command2.Caption = "Admin"
	     End Sub
	
	     Private Sub Command1_Click()
	     'This procedure is an example of allowing the users to change
	     'their own password.
	
	       On Error GoTo ErrorHandler
	
	       Dim En As rdoEnvironment
	       Dim Cn As rdoConnection
	       Dim Ps As rdoPreparedStatement
	       Dim strConnect As String
	       Dim strSQL As String
	       Dim strOldPassword As String
	       Dim strNewPassword As String
	
	       Command2.Enabled = False
	
	       'Change the following to match your values
	       strOldPassword = "OldPwd"
	       strNewPassword = "NewPwd"
	       Set En = rdoEnvironments(0)
	       En.CursorDriver = rdUseOdbc
	
	       strConnect = "Driver={SQL Server};Server=MyServer;" & _
	          "Database=pubs;Uid=UserID;Pwd=" & Trim(strOldPassword)
	
	       Set Cn = En.OpenConnection(dsName:="", Prompt:=rdDriverNoPrompt, _
	       ReadOnly:=False, Connect:=strConnect)
	      'Note that the above is a DSN-less connection
	
	      'Note: If you don't specify master, you will get this following error:
	      '"An invalid parameter was passed."
	
	       strSQL = "{ ? = call master.dbo.sp_password(?,?) }"
	       Set Ps = Cn.CreatePreparedStatement("", strSQL)
	       Ps.rdoParameters(0).Direction = rdParamReturnValue
	       Ps.rdoParameters(1) = strOldPassword
	       Ps.rdoParameters(2) = strNewPassword
	
	       Ps.Execute
	       Debug.Print Ps.rdoParameters(0).Value
	       If Ps.rdoParameters(0) <> 0 Then
	        MsgBox "Could not change password"
	       Else
	        MsgBox "Password has been changed"
	      End If
	      En.Close
	      Ps.Close
	      Cn.Close
	      Unload Me
	     Exit Sub
	
	     ErrorHandler:
	      MsgBox "Error - Password was not changed" & Chr(10) & Chr(13) & Error$
	      En.Close
	     Unload Me
	
	     End Sub
	
	     Private Sub Command2_Click()
	       'This procedure is an example of the SQL Admin changing
	       'a users password.
	       On Error GoTo ErrorHandler
	
	       Dim En As rdoEnvironment
	       Dim Cn As rdoConnection
	       Dim Ps As rdoPreparedStatement
	       Dim strConnect As String
	       Dim strSQL As String
	       Dim strOldPassword As String
	       Dim strNewPassword As String
	       Dim strUserName As String
	
	       Command1.Enabled = False
	
	     'Change the following to match your values
	       strOldPassword = "OldPwd"
	       strNewPassword = "NewPwd"
	       strUserName = "UserID"
	       Set En = rdoEnvironments(0)
	       En.CursorDriver = rdUseOdbc
	
	       strConnect = "Driver={SQL Server};Server=MyServer;" & _
	        "Database=master;Uid=sa;Pwd="
	
	       Set Cn = En.OpenConnection(dsName:="", Prompt:=rdDriverNoPrompt, _
	          ReadOnly:=False, Connect:=strConnect)
	      'Note that the above is a DSN-less connection
	
	       strSQL = "{ ? = call sp_password(?,?,?) }"
	       Set Ps = Cn.CreatePreparedStatement("", strSQL)
	
	       Ps.rdoParameters(0).Direction = rdParamReturnValue
	       Ps.rdoParameters(1) = strOldPassword
	       Ps.rdoParameters(2) = strNewPassword
	       Ps.rdoParameters(3) = strUserName
	
	       Ps.Execute
	       Debug.Print Ps.rdoParameters(0).Value
	       If Ps.rdoParameters(0) <> 0 Then
	         MsgBox "Could not change password"
	       Else
	        MsgBox "Password has been changed"
	       End If
	       En.Close
	       Ps.Close
	       Cn.Close
	       Unload Me
	       Exit Sub
	
	     ErrorHandler:
	     MsgBox "Error - Password was not changed" & Chr(10) & Chr(13) & Error$
	       En.Close
	       Cn.Close
	       Ps.Close
	       Unload Me
	
	     End Sub
	
	Additional query words: rdoquery CreateQuery kbdse kbDSupport kbVBp kbVBp500 kbVBp600 kbVBp400 kbRDO
	
	======================================================================
	Keywords          : kbGrpDSVBDB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500 kbVBA600 kbVB500 kbVB600 kbVB400Search kbVB400
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
