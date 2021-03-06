---
layout: page
title: "Q200296: BUG: ComboBox Display Bleeds Through Pages in a PageFrame"
permalink: /kb/200/Q200296/
---

## Q200296: BUG: ComboBox Display Bleeds Through Pages in a PageFrame

{% raw %}

	Article: Q200296
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:5.0,5.0a,6.0
	Operating System(s): 
	Keyword(s): kbContainer kbCtrl kbvfp500 kbvfp500aBUG kbvfp600 kbvfp600bug kbGrpDSFox kbDSupport kbC
	Last Modified: 07-JUL-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 5.0, 5.0a, 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you place a combo box control, which uses the InteractiveChange event to
	programmatically activate the first page of the pageframe, on the second page of
	a pageframe, when you select an item in that combo box the combo box display
	image bleeds through to the first page.
	
	RESOLUTION
	==========
	
	Here are two possible workarounds for this problem:
	
	- Use a Timer control to activate the first page.
	
	- Place code in the When event of the combo box to set its Visible property to
	  false if the ActivePage of the pageframe is not the second page.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Place the following code into a Visual FoxPro program, and then run the
	  program:
	
	  DIMENSION laComboVals[2]
	  laComboVals[1] = "Choice1"
	  laComboVals[2] = "Choice2"
	
	  oForm = CREATEOBJECT('TestForm')
	  oForm.VISIBLE = .T.
	  READ EVENTS
	
	  **************************************
	  DEFINE CLASS TestForm AS FORM
	    ADD OBJECT pgfTest AS TestPageFrame
	
	    PROCEDURE DESTROY
	      CLEAR EVENTS
	    ENDPROC
	  ENDDEFINE
	
	  DEFINE CLASS TestPageFrame AS PAGEFRAME
	    TOP = 0
	    LEFT = 0
	
	    ADD OBJECT Page1 AS TestPage1
	    ADD OBJECT Page2 AS TestPage2
	  ENDDEFINE
	
	  DEFINE CLASS TestPage1 AS PAGE
	    ADD OBJECT Text1 AS TEXTBOX
	  ENDDEFINE
	
	  DEFINE CLASS TestPage2 AS PAGE
	    ADD OBJECT cboTest1 AS TestCombo1 WITH ;
	      TOP = 10
	    ADD OBJECT cboTest2 AS TestCombo2 WITH ;
	      TOP = 40
	    ADD OBJECT cboTest3 AS TestCombo3 WITH ;
	      TOP = 70
	    ADD OBJECT Timer1 AS Timer1
	      
	    PROCEDURE CLICK
	      THIS.cboTest2.VISIBLE = .T.
	    ENDPROC
	  ENDDEFINE
	
	  DEFINE CLASS TestCombo1 AS COMBOBOX
	    LEFT = 5
	    ROWSOURCETYPE = 5
	    ROWSOURCE = "laComboVals"
	
	    PROCEDURE INTERACTIVECHANGE
	      THIS.PARENT.PARENT.ACTIVEPAGE=1
	      THIS.PARENT.PARENT.Page1.Text1.SETFOCUS()
	      THISFORM.REFRESH()
	    ENDPROC
	  ENDDEFINE
	
	  DEFINE CLASS TestCombo2 AS COMBOBOX
	    LEFT = 5
	    ROWSOURCETYPE = 5
	    ROWSOURCE = "laComboVals"
	    
	    PROCEDURE INTERACTIVECHANGE
	      THIS.PARENT.PARENT.ACTIVEPAGE=1
	      THIS.PARENT.PARENT.Page1.Text1.SETFOCUS()
	      THISFORM.REFRESH()
	    ENDPROC
	    
	    PROCEDURE WHEN
	      IF This.Parent.Parent.ACTIVEPAGE <> 2
	        THIS.VISIBLE = .F.
	      ENDIF
	    ENDPROC
	  ENDDEFINE
	
	  DEFINE CLASS TestCombo3 AS COMBOBOX
	    LEFT = 5
	    ROWSOURCETYPE = 5
	    ROWSOURCE = "laComboVals"
	
	    PROCEDURE INTERACTIVECHANGE
	      THIS.PARENT.Timer1.ENABLED = .T.
	    ENDPROC
	  ENDDEFINE
	
	  DEFINE CLASS Timer1 AS TIMER
	    INTERVAL = 10
	
	    PROCEDURE TIMER
	      THIS.PARENT.PARENT.ACTIVEPAGE=1
	      THIS.PARENT.PARENT.Page1.Text1.SETFOCUS()
	      THISFORM.REFRESH
	      THIS.ENABLED = .F.
	    ENDPROC
	  ENDDEFINE
	
	2. Select an item from each of the combo boxes on page two. The results are:
	
	   - The first (topmost) combo box bleeds through to the first page.
	
	   - The second combo box uses the When event solution so it does not bleed
	     through to the first page.
	
	   - The third combo box uses the Timer solution so it also does not bleed
	     through to the first page.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbContainer kbCtrl kbvfp500 kbvfp500aBUG kbvfp600 kbvfp600bug kbGrpDSFox kbDSupport kbCodeSnippet 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP500 kbVFP600 kbVFP500a
	Version           : WINDOWS:5.0,5.0a,6.0
	Issue type        : kbbug
	Solution Type     : kbnofix
	
	=============================================================================
	

{% endraw %}
