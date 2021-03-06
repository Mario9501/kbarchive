---
layout: page
title: "Q142928: PRB: Bound ListBox Doesn't Show List Item When MultiSelect = 2"
permalink: /kb/142/Q142928/
---

## Q142928: PRB: Bound ListBox Doesn't Show List Item When MultiSelect = 2

{% raw %}

	Article: Q142928
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 
	Operating System(s): 
	Keyword(s): kbGrpDSVBDB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	- Microsoft Visual Basic Standard Edition for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 4.0 
	- Microsoft Visual Basic Standard Edition for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If you set the MultiSelect property of a bound Standard ListBox control at
	design time to 2-Extended, and then run the application, you can MultiSelect
	with CTRL+Click but the control is not bound to the Data control at this time.
	When you go back into design mode, the MultiSelect property is reset to 0-None,
	then when you run again, you get the correct behavior.
	
	CAUSE
	=====
	
	This is a behavior of Visual Basic. It is not practical to select multiple items
	from a listbox that is bound to only a single column of a data control. If you
	set the MultiSelect property of the control to 2-Extended, Visual Basic should
	reset it back to 0-None before going into run mode, not after it returns from
	the first run. This way it will not appear that you can almost get MultiSelect
	to work with a bound listbox.
	
	RESOLUTION
	==========
	
	Do not set the MultiSelect Property of a bound standard ListBox control to
	2-Extended as it will cause this misleading behavior.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Problem in Visual Basic Version 4.0
	------------------------------------------------------
	
	1. Start a new project in Visual Basic. Form1 is created by default.
	
	2. Add a Data control to Form1.
	
	3. Connect Data1 on Form1 to a table in a database as follows: Select the Data
	  control and press the F4 key to display the Properties window. Set the
	  DatabaseName property to BIBLIO.MDB, and set the RecordSource property to the
	  source table name Publishers.
	
	4. Add a Standard ListBox control to Form1. Select the ListBox control and press
	  the F4 key to display the Properties window. Set the DataSource property to
	  Data1, the DataField property to State, and the MultiSelect property to
	  2-Extended.
	
	5. Add the following to the Form Load event code:
	
	     Private Sub Form_Load()
	       List1.AddItem "CA"
	       List1.AddItem "WA"
	       List1.AddItem "PA"
	       List1.AddItem "MA"
	       List1.AddItem "IL"
	       List1.AddItem "FL"
	     End Sub
	
	6. Start the program, or press the F5 key. Click next and previous on the data
	  control and notice how the selection on the listbox does not change even
	  though it is bound to the Data control. You can MultiSelect with CTRL+Click.
	  When you go back into design mode the MultiSelect property is reset to
	  0-None, then when you run again, you get the correct behavior.
	
	Additional query words: kbVBp400 kbVBp600 kbdse kbDSupport kbVBp kbControl
	
	======================================================================
	Keywords          : kbGrpDSVBDB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVBA600 kbVB600 kbVB400Search kbVB400
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
