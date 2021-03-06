---
layout: page
title: "Q138043: PRB: Error Instantiating Object"
permalink: /kb/138/Q138043/
---

## Q138043: PRB: Error Instantiating Object

{% raw %}

	Article: Q138043
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:3.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 04-AUG-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	CreateObject(), when used with a class defined from a wizard-generated form,
	produces this error:
	
	  Error Instantiating Object
	
	CAUSE
	=====
	
	When you save a form as a class, you lose the DataEnvironment information. Also,
	the wizard-generated code is brought beyond its original scope, therefore an
	instance cannot be generated.
	
	RESOLUTION
	==========
	
	Recreate the original form by hand, and then recreate the class. Creating the
	DataEnvironment before instantiating the object will get you around the error,
	but not the loss of functionality and other wizard-generated form class issues.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	NOTE: The wizard-generated code is no longer part of any explicit event, which
	causes a number of variables to either fall out of scope, or not be initialized
	properly, and will result in multiple runtime errors. This will cause the
	creation of an instance and/or the use of the form as a class to fail.
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Using the Form Wizard, create a form, and save it as a class called Mine in
	  the library Myclass.
	
	2. Run the following in a program:
	
	     SET CLASSLIB TO D:\Vfp\Myclass ADDITIVE
	     x = CreateObject('Mine')
	     && The error occurs here
	     x.Show
	     READ EVENTS
	
	(c) Microsoft Corporation 2000, All Rights Reserved. Contributions by Kevin
	Zollman, Microsoft Corporation.
	
	
	Additional query words: VFoxWin akz
	
	======================================================================
	Keywords          :  
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300
	Version           : WINDOWS:3.0
	
	=============================================================================
	

{% endraw %}
