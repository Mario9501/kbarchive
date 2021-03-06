---
layout: page
title: "Q155976: PRB: Output from SourceSafe Command Lines Is Truncated"
permalink: /kb/155/Q155976/
---

## Q155976: PRB: Output from SourceSafe Command Lines Is Truncated

{% raw %}

	Article: Q155976
	Product(s): Microsoft SourceSafe
	Version(s): WINDOWS:3.04,3.1,4.0,4.0a,5.0,6.0
	Operating System(s): 
	Keyword(s): kbSSafe400 kbSSafe500 kbSSafe600 kbSSafe310 kbSSafe304
	Last Modified: 01-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual SourceSafe for Windows, versions 4.0, 4.0a, 5.0, 6.0 
	- Microsoft SourceSafe for Windows, versions 3.04, 3.1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When using certain combinations of the SourceSafe Command line to display
	information, filenames may appear truncated. This will occur if the filename
	being displayed is greater than 19 characters in length.
	
	CAUSE
	=====
	
	It may be desirable to redirect or print the output from certain SourceSafe
	Command lines. To ensure that this output appears in a presentable format, long
	filenames may be truncated to maintain an even columnar layout.
	
	RESOLUTION
	==========
	
	The above truncation will appear only against files that are checked out. Files
	containing greater than 19 characters that are not checked out will have their
	entire filename displayed.
	
	As an alternative, you can instruct SourceSafe to display filenames in their 8.3
	DOS format. This option will display the entire DOS filename. For example,
	running the Command line:
	
	  SS DIR -E -NS
	
	against the database described in the Steps to Reproduce Problem section of this
	article will generate output that uses the file's 8.3 DOS format name. All other
	information is displayed as expected. -NS instructs SourceSafe to use "short"
	filenames, -NL is used for long filenames.
	
	NOTE: When using short filenames in SourceSafe, you may combine the -NS switch
	with other Command line options, such as ADD, CHECKIN, and CHECKOUT.
	
	STATUS
	======
	
	Microsoft is researching this problem and will post new information here in the
	Microsoft Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Problem
	--------------------------
	
	1. Create or locate a file whose name contains more than 19 characters.
	
	2. Run or switch to Visual SourceSafe and add the file from step 1 to the root
	  project ($/).
	
	3. Check out the file, and then Close Visual SourceSafe.
	
	4. Open a DOS window.
	
	5. If you are running Visual SourceSafe, switch to the VSS\WIN32. Otherwise,
	  switch to the SS\WINNT directory.
	
	6. Enter the following Visual SourceSafe Command line:
	
	  SS DIR -E
	
	  Note that the first 19 characters of the added file are displayed while the
	  remaining characters are truncated. This same effect is visible from other
	  SourceSafe commands such as:
	
	  SS STATUS
	
	Additional query words:
	
	======================================================================
	Keywords          : kbSSafe400 kbSSafe500 kbSSafe600 kbSSafe310 kbSSafe304 
	Technology        : kbSSafeSearch kbAudDeveloper kbZNotKeyword3 kbSSafe304 kbSSafe310 kbSSafe600 kbSSafe400 kbSSafe400a kbSSafe500
	Version           : WINDOWS:3.04,3.1,4.0,4.0a,5.0,6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
