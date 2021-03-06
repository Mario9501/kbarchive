---
layout: page
title: "Q114256: How to Duplicate Varying Number of Labels Per Record"
permalink: /kb/114/Q114256/
---

## Q114256: How to Duplicate Varying Number of Labels Per Record

{% raw %}

	Article: Q114256
	Product(s): Microsoft FoxPro
	Version(s): MS-DOS:2.5,2.5a,2.5b,2.6; WINDOWS:2.5,2.5a,2.5b,2.6,3.0
	Operating System(s): 
	Keyword(s): kbcode
	Last Modified: 09-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	- Microsoft FoxPro for Windows, versions 2.5, 2.5a, 2.5b, 2.6 
	- Microsoft FoxPro for MS-DOS, versions 2.5, 2.5a, 2.5b, 2.6 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	While article Q106030, "How to Print Multiple Copies of the Same Label",
	describes a method to produce a fixed number of duplicate labels, this article
	addresses those situations where the number of times each label is to be
	duplicated must vary.
	
	MORE INFORMATION
	================
	
	This example uses the following files:
	
	  XLABEL.DBF - label data records with an additional count field (DUP)
	  DUPLIX.DBF - database that holds the duplicated records; recreated each
	               session
	  DUPLABEL.LBX (and .LBT) - label layout form referencing DUPLIX fields
	  DUPLABEL.PRG - program that fills DUPLIX database with duplicates
	
	To set up the files:
	
	1. Create (or modify) the data file (XLABEL.DBF) structure to contain a numeric
	  field (DUP) that will hold the number that indicates how many times each
	  label is to be copied.
	
	2. To create DUPLIX, issue this command:
	
	        CREATE duplix
	
	  DUPLIX contains those fields from XLABEL.DBF that will be used by the label
	  form. If you want all the fields, issue the following commands, and then
	  remove the count field DUP from the DUPLIX structure:
	
	        USE XLABEL
	        COPY STRUCTURE to DUPLIX
	
	3. Issue the following command, using the fields found in DUPLIX:
	
	        CREATE LABEL DUPLABEL
	
	  In Visual FoxPro, add the DUPLIX table to the Data Environment of the label.
	
	4. Issue the MODIFY COMMAND DUPLABEL command, and then enter the following
	  code:
	
	        SET TALK OFF
	
	        * Open databases.
	        IF USED('DUPLIX')
	           SELECT duplix
	        ELSE
	           USE duplix
	        ENDIF
	        SELECT 0
	        IF USED('XLABEL')
	           SELECT xlabel
	        ELSE
	           USE xlabel
	        ENDIF
	
	        * Create blank merge file.
	        SET SAFETY OFF
	        SET TEXTMERGE TO hold
	        SET SAFETY ON
	        SET TEXTMERGE ON NOSHOW
	
	        * Cycle through labels, outputting each to the HOLD file
	        * for the number of times stated in XLABEL.DUP field.
	        SCAN
	           FOR i=1 TO xlabel.dup
	              \\<<xlabel.co>><<xlabel.contact>><<xlabel.addr>>
	              \ 
	           ENDFOR
	        ENDSCAN
	        * NOTE: The double backslash prevents an initial carriage return,
	        * which would result in the first label being blank when printed.
	
	        * Close the merge file.
	        SET TEXTMERGE OFF
	        SET TEXTMERGE TO
	
	        * Prepare the DUPLIX database to receive the new labels.
	        SELECT duplix
	        SET SAFETY OFF
	        ZAP
	        SET SAFETY ON
	
	        * Add in the new labels to the blank DUPLIX database.
	        APPEND FROM hold.txt TYPE SDF
	
	        * Send out the labels.
	        LABEL FORM duplabel PREVIEW
	
	NOTE: The PREVIEW option can be replaced by or used with TO PRINT to send the
	labels to the printer.
	
	Additional query words: VFoxWin FoxDos FoxWin repeat
	
	======================================================================
	Keywords          : kbcode 
	Technology        : kbVFPsearch kbAudDeveloper kbFoxproSearch kbZNotKeyword3 kbFoxPro250DOS kbFoxPro250aDOS kbFoxPro250bDOS kbFoxPro260DOS kbFoxPro260 kbFoxPro250 kbFoxPro250a kbFoxPro250b kbVFP300
	Version           : MS-DOS:2.5,2.5a,2.5b,2.6; WINDOWS:2.5,2.5a,2.5b,2.6,3.0
	
	=============================================================================
	

{% endraw %}
