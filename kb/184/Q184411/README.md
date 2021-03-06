---
layout: page
title: "Q184411: FP: Cannot Validate Form Field if Name Has Invalid Character"
permalink: /kb/184/Q184411/
---

## Q184411: FP: Cannot Validate Form Field if Name Has Invalid Character

{% raw %}

	Article: Q184411
	Product(s): Word Front Page
	Version(s): MACINTOSH:1.0; WINDOWS:97
	Operating System(s): 
	Keyword(s): kbdta
	Last Modified: 04-OCT-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft FrontPage 97 for Windows with Bonus Pack 
	- Microsoft FrontPage for the Macintosh, version 1.0 
	-------------------------------------------------------------------------------
	
	For a Microsoft FrontPage 2000 version of this article, see Q205545.
	
	For a Microsoft FrontPage 98 version of this article, see Q194283.
	
	SYMPTOMS
	========
	
	If the Name property of a form field contains an invalid character and you
	attempt to use form field validation on that field, you will receive one of the
	following messages depending on the version of FrontPage you are using.
	
	FrontPage 97
	------------
	
	  This control's name is not a valid identifier for scripting languages.
	  Consequently, any script that FrontPage generates may not work properly.
	  Before specifying validation criteria, please change the control's name so
	  that it starts with a letter, and subsequent characters are letters (A-Z and
	  a-z), digits (0-9), or underscores ("_").
	
	NOTE: The letters must be ASCII; extended characters are not allowed.
	
	FrontPage for the Macintosh 1.0
	-------------------------------
	
	  This control's name is not a valid identifier for scripting languages. Use
	  ASCII letters, digits, or underscores.
	
	CAUSE
	=====
	
	The scripting language used by FrontPage does not recognize spaces or extended
	characters (such as /, \, *, &, @, and so forth) as valid characters for a
	form field name. Form field validation will not work if you use any of these
	characters in the Name property of a form field.
	
	RESOLUTION
	==========
	
	Remove the invalid characters or spaces from the form field names.
	
	1. Click the form field that you want to modify.
	
	2. On the Edit menu, click Form Field Properties.
	
	3. In the Name box, type a name that contains alphanumeric characters, such as
	  A-Z, a-z, or 0-9 or the underscore character ("_"). The name must start with
	  a letter.
	
	
	Additional query words: 97 validate form field
	
	======================================================================
	Keywords          : kbdta 
	Technology        : kbHWMAC kbOSMAC kbFrontPageSearch kbZNotKeyword8 kbFrontPage97Search kbFrontPageMac kbZNotKeyword3
	Version           : MACINTOSH:1.0; WINDOWS:97
	Hardware          : MAC x86
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
