---
layout: page
title: "Q195087: HOWTO: Enable Communications Between UserDocuments/UserControls"
permalink: /kb/195/Q195087/
---

## Q195087: HOWTO: Enable Communications Between UserDocuments/UserControls

{% raw %}

	Article: Q195087
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:5.0,6.0
	Operating System(s): 
	Keyword(s): kbcode kbCtrl kbVBp kbVBp500 kbVBp600 kbGrpDSVBDB kbCodeSam
	Last Modified: 24-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article covers how to enable communications between UserControls and
	UserDocuments and other programs. There are times when both UserControls and
	UserDocuments need to communicate with other forms that are part of the entire
	program. Making public functions and public subroutines only enables
	communications from parent forms and processes. Using GLOBAL instead of PUBLIC
	allows information to be shared between controls, classes, and forms.
	
	MORE INFORMATION
	================
	
	The project code below is an example of Global Variables being shared:
	
	1. Create a Standard EXE project in Visual Basic. Form1 is created by default.
	
	2. Select ActiveX Document EXE.
	
	3. Add two additional UserDocuments and one module to the project. Cut and paste
	  the following code into the module's code pane:
	
	        Option Explicit
	
	        Global MyNumber As Variant
	
	4. For Document1, add two commandbuttons, a label. and one textbox. Place the
	  label above the textbox and clear text1.Text. Cut and paste the following
	  code into its code pane:
	
	        Private Sub UserDocument_Initialize()
	           Command2.Caption = ">>"
	           Label1.Caption = "Set the number below"
	        End Sub
	
	        Private Sub Command1_Click()
	           MyNumber = Text1.Text
	        End Sub
	
	        Private Sub Command2_Click()
	           UserDocument.Hyperlink.NavigateTo App.Path & "\UserDocument2.Vbd"
	        End Sub
	
	5. For Document2, add two command buttons, a label and one textbox. Place the
	  label above the textbox and clear text1.Text. Cut and paste the following
	  code into its code pane:
	
	        Private Sub Command1_Click()
	           UserDocument.Hyperlink.GoBack
	        End Sub
	
	        Private Sub Command2_Click()
	           UserDocument.Hyperlink.NavigateTo App.Path & "\UserDocument3.vbd"
	        End Sub
	
	        Private Sub UserDocument_Initialize()
	           Command1.Caption = "<<"
	           Command2.Caption = ">>"
	           Label1.Caption = "The Magic Number Is"
	            Text1.Text = MyNumber
	        End Sub
	
	6. For Document3, add two command buttons, a label and one textbox. Place the
	  label above the textbox and clear text1.Text. Cut and paste the following
	  code into its code pane:
	
	        Private Sub Command1_Click()
	          UserDocument.Hyperlink.GoBack
	        End Sub
	
	        Private Sub UserDocument_Initialize()
	          Command1.Caption = "<<"
	          Label1.Caption = "The Magic Number Is"
	          Text1.Text = MyNumber
	        End Sub
	
	7. Run the project. Type a number in the text box and click the Command1 button.
	  Next, navigate to the other two documents and notice your number shows up.
	  Navigate back. When you navigate back to UserDocument1, the number you placed
	  in the text will be gone. Also notice that no matter how many times you
	  navigate back and forth between the documents, the number you added to the
	  Global variable is always the same and always available.
	
	REFERENCES
	==========
	
	For more information about UserControls and UserDocuments, use VB Help and query
	UserControls or UserDocuments.
	
	(c) Microsoft Corporation 1998, All Rights Reserved. Contributions by Richard T.
	Edwards, Microsoft Corporation
	
	
	Additional query words: kbDSupport Kbdse
	
	======================================================================
	Keywords          : kbcode kbCtrl kbVBp kbVBp500 kbVBp600 kbGrpDSVBDB kbCodeSam 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVB500 kbVB600
	Version           : WINDOWS:5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
