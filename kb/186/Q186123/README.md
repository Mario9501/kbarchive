---
layout: page
title: "Q186123: BUG: The Coolbar ActiveX Control Does Not Work in VFP"
permalink: /kb/186/Q186123/
---

## Q186123: BUG: The Coolbar ActiveX Control Does Not Work in VFP

{% raw %}

	Article: Q186123
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 04-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The Coolbar ActiveX control works with products such as Microsoft Internet
	Explorer, Visual C++, and Visual Basic. Unfortunately, this ActiveX control does
	not work in Visual FoxPro.
	
	RESOLUTION
	==========
	
	Do not use the Coolbar ActiveX control in Visual FoxPro.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	MORE INFORMATION
	================
	
	The Coolbar ActiveX control is a container control that consists of a collection
	of "Band" objects used to create a configurable toolbar that is associated with
	a form. A Coolbar control typically contains two or more Bands, which the user
	may resize and rearrange. Each of these Bands contains a single child control.
	The problems occur because Visual FoxPro can not process the messages from these
	child controls in the Band; therefore, erratic responses occur. In fact, Visual
	FoxPro cannot handle any ActiveX controls that support containership.
	
	Some symptoms of the erratic behavior exhibited by the Coolbar control when used
	in Visual FoxPro are:
	
	1. The Coolbar control appears on a form at design time but is invisible at
	  run-time. Although the Coolbar control is invisible at run-time, any FoxPro
	  controls that you place in the Coolbar control appear on the form at
	  run-time.
	
	2. Dropping a FoxPro control that contains "white space", such as a text box,
	  combo box, or spinner, onto the Coolbar control while the control is in Edit
	  mode, causes the FoxPro control to flash in design mode. The flashing does
	  not occur at run-time.
	
	3. Dropping a FoxPro control that has a caption on it, such as a command button,
	  check box, or option group, results in the caption becoming invisible at both
	  design time and run-time. You must access the Coolbar control's Property
	  sheet at least once to see this behavior. If you have never opened the
	  Coolbar control's property sheet, the captions will be visible.
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a form in Visual FoxPro and add the FoxPro OLE Container control.
	
	2. In the Insert Object dialog box, select the "Create Control" option button,
	  choose the Microsoft Coolbar control from the list and then press OK.
	
	3. Select the FoxPro check box control located on the Form Control's toolbar.
	  Next, click inside the Coolbar control's body to add the check box to the
	  Coolbar control. Note that the check box flashes inside the Coolbar control
	  while you are modifying the form.
	
	4. Run the form. Note that the check box control does not flash at run- time and
	  that the Coolbar control is invisible at run-time.
	
	5. Modify the form and right-click the Coolbar control. From the shortcut menu
	  select "Microsoft Coolbar control properties". Click OK to close the Property
	  sheet. Note that the caption of the check box is not visible in either design
	  or run-time.
	
	Additional query words: kbvfp600
	
	======================================================================
	Keywords          :  
	Technology        : kbVFPsearch kbAudDeveloper kbVFP600
	Version           : WINDOWS:6.0
	Issue type        : kbbug
	Solution Type     : kbnofix
	
	=============================================================================
	

{% endraw %}
