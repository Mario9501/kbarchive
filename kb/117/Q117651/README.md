---
layout: page
title: "Q117651: PC Forms: Err Msg: Invalid Package When Sending an E-Form"
permalink: /kb/117/Q117651/
---

## Q117651: PC Forms: Err Msg: Invalid Package When Sending an E-Form

{% raw %}

	Article: Q117651
	Product(s): Microsoft Mail For PC Networks
	Version(s): WINDOWS:1.0,3.0,3.2
	Operating System(s): 
	Keyword(s): 
	Last Modified: 16-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Electronic Forms Designer, version 1.0, used with:
	   - Microsoft Mail for PC Networks, versions 3.0, 3.2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	In version 1.0 of Microsoft Electronic Forms Designer, an attempt to send a
	message created using an E-form may generate this error message:
	
	  Invalid Package
	
	CAUSE
	=====
	
	The startup form for the E-form Visual Basic project is set incorrectly.
	
	RESOLUTION
	==========
	
	In order for an E-form to initialize correctly, the startup form for the Visual
	Basic project must be set to the Sub Main procedure, rather than to a Visual
	Basic form.
	
	To set the Startup Form to Sub Main, follow these steps:
	
	1. Open the E-form project in Visual Basic.
	
	2. From the Options menu, select Project.
	
	3. Locate the Startup Form option.
	
	4. Click on the list box to display the Setting options.
	
	5. Select Sub Main.
	
	This sets the Sub Main procedure to run when the E-form is started, properly
	initializing the E-form package.
	
	
	Additional query words: 1.00
	
	======================================================================
	Keywords          :  
	Technology        : kbZNotKeyword2 kbMailSearch kbZNotKeyword3
	Version           : WINDOWS:1.0,3.0,3.2
	
	=============================================================================
	

{% endraw %}
