---
layout: page
title: "Q158256: BUG: AFIELDS() Array Causes Error in CREATE...FROM ARRAY"
permalink: /kb/158/Q158256/
---

## Q158256: BUG: AFIELDS() Array Causes Error in CREATE...FROM ARRAY

{% raw %}

	Article: Q158256
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:5.0,5.0a,6.0
	Operating System(s): 
	Keyword(s): kbprogramming kbvfp kbvfp500aBUG kbvfp500bugkbbuglist
	Last Modified: 11-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 5.0, 5.0a, 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you create a table from the table structure contained in an array built by
	Visual FoxPro 5.0 or 6.0's AFIELDS() function, a message dialog box informs you
	that the table name you specified for that new table is already used for another
	object. The dialog box asks you to choose another table name.
	
	The dialog box options are OK and HELP. When you click OK, the new table is
	created with the name you originally specified. However, the new table contains
	a back-link to the database containing the source table, which you will discover
	the next time you "USE" the new table.
	
	CAUSE
	=====
	
	New to Visual FoxPro 5.0 are the 12th through 16th columns of the AFIELDS()
	array. The 12th column contains the long file name of the table. The CREATE ...
	FROM ARRAY command sees this value and interprets it to mean the new table
	should have the same value. This triggers the message dialog box to the user.
	
	When the user responds, other functionality in the CREATE ...FROM ARRAY command
	proceeds to create the desired table with the name the user specified.
	
	Erroneously, the CREATE ... FROM ARRAY command then includes the back link from
	the original table, based on the (long) file name value in column 12 of the
	array.
	
	When the new table is being opened in a work area, a dialog box states that
	"<the database in the back-link> cannot link table <the table to be
	opened> to the database: duplicate or missing fields. Would you like to try
	to locate the owning database or delete the link (and free the table)?"
	
	WORKAROUND
	==========
	
	The problem is two-fold. When the first dialog box appears, click OK to create
	the table.
	
	When the second dialog box appears, choose the Delete option to delete the
	back-link and free the table. If you then want the new table to belong to a
	database, you need to deliberately add it to that database.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products listed at
	the beginning of this article. We are researching this problem and will post new
	information here in the Microsoft Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. In the Command window enter the following commands:
	
	        CREATE DATABASE mydata
	        CREATE TABLE mytable (mychar c(1))
	        =AFIELDS(laStru)
	        CREATE TABLE another_table FROM ARRAY laStru
	
	2. When the following dialog box appears, click the OK button.
	
	  The name mytable is already used for another object. Please choose a
	  different name.
	
	  Then enter the following command:
	
	  " USE another_table " (without the quotation marks)
	
	3. When the following dialog box appears, click Delete:
	
	  C:\Vfp50\mydata.dbc cannot link table C:\Vfp50\another_table.dbf to this
	  database: duplicate or missing fields. Would you like to try to locate the
	  owning database or delete the link (and free the table)?
	
	  (The path shown above is different to reflect the actual path to the
	  database.dbc and table.dbf on your system.)
	
	The empty table "another_table" can now be seen in a work area.
	
	Additional query words: kbvfp500 kbvfp600
	
	======================================================================
	Keywords          : kbprogramming kbvfp kbvfp500aBUG kbvfp500bug kbbuglist
	Technology        : kbVFPsearch kbAudDeveloper kbVFP500 kbVFP600 kbVFP500a
	Version           : WINDOWS:5.0,5.0a,6.0
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
