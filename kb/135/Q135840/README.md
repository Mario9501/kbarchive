---
layout: page
title: "Q135840: INF: Use of SQLBindParameter with VB and an ODBC driver"
permalink: /kb/135/Q135840/
---

## Q135840: INF: Use of SQLBindParameter with VB and an ODBC driver

{% raw %}

	Article: Q135840
	Product(s): Open Database Connectivity (ODBC)
	Version(s): WINDOWS:2.0,3.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 12-JUN-2001
	
	3.00 2.00
	
	WINDOWS
	
	kbprg kbcode
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Open Database Connectivity, version 2.0 
	- Microsoft Visual Basic Standard Edition for Windows, version 3.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This sample Visual Basic (VB) code illustrates the use of the ODBC API call
	SQLBindParameter() with a VB string variable. It has been kept as simple as
	possible with a minimal amount of code and declarations.
	
	For more information on calling Windows APIs from Visual Basic, refer to the
	document "Ten Commandments for Accessing the Windows API" written by Daniel
	Appleman of Desaware and available on the Microsoft Developer Network (MSDN)
	Level 1 CD.
	
	MORE INFORMATION
	================
	
	Declarations required to call ODBC API from VB 3.0:
	
	     Declare Function GetFocus Lib "User" () As Integer
	     Declare Function GetParent Lib "User" (ByVal hWnd%) As Integer
	     Declare Function SQLAllocConnect Lib "odbc.dll" (ByVal henv&, phdbc&)
	     As Integer
	     Declare Function SQLAllocEnv Lib "odbc.dll" (phenv&) As Integer
	     Declare Function SQLAllocStmt Lib "odbc.dll" (ByVal hdbc&, phstmt&) As
	     Integer
	     Declare Function SQLDisconnect Lib "odbc.dll" (ByVal hdbc&) As Integer
	     Declare Function SQLError Lib "odbc.dll" (ByVal henv&, ByVal hdbc&,
	     ByVal hstmt&, ByVal szSqlState$, pfNativeError&, ByVal szErrorMsg$,
	     ByVal cbErrorMsgMax%, pcbErrorMsg%) As Integer
	     Declare Function SQLExecDirect Lib "odbc.dll" (ByVal hstmt&, ByVal
	     szSqlStr$, ByVal cbSqlStr&) As Integer
	     Declare Function SQLFetch Lib "odbc.dll" (ByVal hstmt&) As Integer
	     Declare Function SQLFreeConnect Lib "odbc.dll" (ByVal hdbc&) As Integer
	     Declare Function SQLFreeEnv Lib "odbc.dll" (ByVal henv&) As Integer
	     Declare Function SQLFreeStmt Lib "odbc.dll" (ByVal hstmt&, ByVal
	     fOption%) As Integer
	
	You should pay particular attention to the declaration of any string variable
	that will need to be passed to ODBC.DLL. This includes rgbValue in both
	SQLBindParameter() and SQLGetData(). The declaration should be "rgbValue as Any"
	to work. This is the most flexible way to declare a function variable for a
	Windows DLL function that will be passed from a VB program in a Windows DLL
	because it allows for both string and numeric values to be passed. When a string
	value is passed from a VB program to the Windows DLL and the DLL call expects a
	'char *', then the VB program should declare the variable being passed as a VB
	String variable, and then pass it with the ByVal indicator. This is what is
	shown in the example here. If the VB variable to be passed had been a numeric
	value, then the variable that would be passed could be declared as long or
	integer, and during the call to the DLL, the variable would go into the call
	without the ByVal modifier.
	
	The reason this happens is that in all cases, the C function expects a pointer to
	a memory location. From VB's perspective, a String variable refers to a pointer
	to a pointer to a memory location containing a string. This is why ByVal used in
	front of the variable during the function call gives a pointer to a memory
	location containing a string. On the other hand, a numeric variable in VB refers
	to a pointer to a memory location containing a numeric value. That is why the
	ByVal modifier is not necessary for the function call when a numeric VB variable
	is being passed in.
	
	     Declare Function SQLGetData Lib "odbc.dll" (ByVal hstmt&, ByVal
	     icol%, ByVal fCType%, rgbValue As Any, ByVal cbValueMax&, pcbValue As
	     Long) As Integer
	     Declare Function SQLBindParameter Lib "odbc.dll" (ByVal hstmt&, ByVal
	     ipar%, ByVal fParamType%, ByVal fCType%, ByVal fSqlType%, ByVal
	     cbColDef&, ByVal ibScale%, rgbValue As Any, ByVal cbValueMax&,
	     pcbValue As Long) As Integer
	
	     Declare Function SQLDriverConnect Lib "odbc.dll" (ByVal hdbc&, ByVal
	     hWnd%, ByVal szCSIn$, ByVal cbCSIn%, ByVal szCSOut$, ByVal cbCSMax%,
	     cbCSOut%, ByVal fDrvrComp%) As Integer
	     Declare Function SQLParamData Lib "odbc.dll" (ByVal hstmt&, prgbValue
	     As Any) As Integer
	     Declare Function SQLPutData Lib "odbc.dll" (ByVal hstmt&, rgbValue As
	     Any, ByVal cbValue&) As Integer
	
	     Const SQL_ERROR = -1
	     Const SQL_C_DEFAULT = 99
	
	     Const SQL_CHAR = 1
	     Const SQL_C_CHAR = 1
	
	     Const SQL_NEED_DATA = 99
	
	     Const SQL_LONGVARCHAR = -1
	     Const SQL_BINARY = -2
	     Const SQL_VARBINARY = -3
	     Const SQL_LONGVARBINARY = -4
	
	     Const SQL_C_BINARY = SQL_BINARY
	
	     Const SQL_DRIVER_PROMPT = 2
	
	     Const SQL_LEN_DATA_AT_EXEC_OFFSET = -100
	
	     Sub Command3D1_Click()
	
	This sample VB code illustrates the use of the ODBC API call SQLBindParameter().
	It has been kept as simple as possible with a minimal amount of code and
	declarations.
	
	      Dim henv As Long
	      Dim hdbc As Long
	      Dim hstmt As Long
	      Dim nstatus%
	      Dim buffer As String
	      Dim param As String
	
	      nstatus = SQLAllocEnv(henv)
	
	      nstatus = SQLAllocConnect(henv, hdbc)
	      If (nstatus = SQL_ERROR) Then
	          MsgBox "Couldn't allocate memory for connection"
	      End If
	
	The parameters passed to SQLDriverConnect() after the second one are not really
	used for anything. The call expects the variables as output variables so we pass
	them to the call to problems.
	
	     nstatus = SQLDriverConnect(hdbc, GetParent(GetFocus()), S$,
	     Len(S$), Server, Len(Server), cbOut%, SQL_DRIVER_PROMPT)
	      If (nstatus = SQL_ERROR) Then
	          MsgBox "Couldn't connect"
	      End If
	
	In this sample, you are connecting to a SQL Server database and define this
	table:
	
	  CREATE TABLE model01 (col1 char(30),col2 char(30))
	
	after you have executed the following insert statement:
	
	  INSERT INTO model01 VALUES ("Kate Moss","Elite")
	
	For simplicity, assume only one row in the table.
	
	      sSQLString = "Select * from model01 where col2 = ?"
	
	      leng = Len(sSQLString)
	
	      nstatus = SQLAllocStmt(hdbc, hstmt)
	      If (nstatus = SQL_ERROR) Then
	          MsgBox "Couldn't allocate memory for statement"
	      End If
	
	At this point, assign a value to the variable "param" that is going to be bound
	to the SQL statement via SQLBindParameter(). After this binding, the SQL
	statement becomes:
	
	  select * from model01 where col2 = 'Elite'
	
	It is not a requirement of the VB programmer to put the single quotation marks
	into the parameter marker (param). This is handled by ODBC.
	
	  param = "Elite"
	
	In this particular call to SQLBindParameter, you are binding a VB string variable
	to a column on the SQL Server database server that is a char(30). The '1' in the
	third parameter of this call indicates that this parameter is of type
	SQL_PARAM_INPUT. For more information, refer to the definition of fParamType in
	the description of SQLBindParameter() in the "Microsoft ODBC 2.0 Programmer's
	Reference and SDK Guide."
	
	The sixth parameter, cbColDef, is indicating that you will be binding to a column
	that is 30 bytes long on SQL Server. This could also be determined with
	SQLColumns() but is assumed here to keep this example small and simple.
	
	The 7th parameter (ibScale) is zero because Appendix D of the ODBC 2.0
	Programmer's Reference states that this is the case for char datatypes. The 8th
	parameter is a pointer to the VB SQLGetData() and the VB variable "param". Note
	that the ByVal in the passing of the VB variable called buffer is very important
	for this call to succeed. The 9th parameter is 300 because you should not return
	more than 300 bytes through this parameter. And the final parameter indicates
	that the parameter is a null-terminated string (SQL_NTS as defined in
	C:\ODBCSDK\INCLUDE\SQL.H).
	
	  nstatus = SQLBindParameter(hstmt, 1, 1, SQL_C_CHAR, SQL_CHAR, 30,
	     0, ByVal param, 300, -3)
	      If (nstatus = SQL_ERROR) Then
	          MsgBox "error on Bind"
	      End If
	
	Send the SQL statement, which is now in the form:
	
	     select * from model01 where col2 = 'Elite'
	
	      nstatus = SQLExecDirect(hstmt, sSQLString, leng)
	      If (nstatus = SQL_ERROR) Then
	          MsgBox "Error on execdirect"
	      End If
	
	Fetch back the first row of data. To keep this example simple, assume that this
	is the only row of data in the table that is of concern and fetch that.
	Normally, you should keep calling SQLFetch() and SQLGetData() in a loop until
	SQLFetch() returns 100 as a return code(SQL_NO_DATA_FOUND as defined in SQL.H).
	
	      nstatus = SQLFetch(hstmt)
	      If (nstatus = SQL_ERROR) Then
	          MsgBox "Error on fetch"
	      End If
	
	It is important to initialize the VB variable that is being passed into
	SQLGetData() to return the data that was just fetched back. Otherwise, it may
	not be returned correctly or at all.
	
	  buffer = String$(300, 0)
	
	Bring the data returned to the client workstation via SQLFetch() into the VB
	program via SQLGetData() and the VB variable "buffer". Note that the ByVal in
	the passing of the VB variable called buffer is very important for this call to
	succeed.
	
	     nstatus = SQLGetData(hstmt, 1, SQL_C_CHAR, ByVal buffer, Len(buffer),
	     300
	     )
	      If (nstatus = SQL_ERROR) Then
	          MsgBox "Error on getdata"
	      End If
	
	Print the data just fetched back onto the screen.
	
	       MsgBox "buffer contains => " + buffer
	
	Here, do a quick cleanup of the environment. Notice that you do not need to call
	SQLFreeStmt():
	
	      nstatus = SQLDisconnect(hdbc)
	      nstatus = SQLFreeConnect(hdbc)
	      nstatus = SQLFreeEnv(henv)
	
	      MsgBox "Finished"
	     End Sub
	
	Additional query words: 3.00 function odbcsdk ref
	
	======================================================================
	Keywords          :  
	Technology        : kbVBSearch kbAudDeveloper kbODBCSearch kbVB300Search kbVB300 kbODBC200
	Version           : WINDOWS:2.0,3.0
	
	=============================================================================
	

{% endraw %}
