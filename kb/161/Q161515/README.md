---
layout: page
title: "Q161515: WD97: Macro Virus Warning Displayed When No Macros Exist in File"
permalink: /kb/161/Q161515/
---

## Q161515: WD97: Macro Virus Warning Displayed When No Macros Exist in File

{% raw %}

	Article: Q161515
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbdta word8 word97kbfaq
	Last Modified: 14-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you open a Word 97 document or template, you get the following macro virus
	warning, although the document or template does not contain any macros:
	
	  The document you are opening contains macros or customizations. Some macros
	  contain viruses that could harm your computer.
	
	  If you are sure this document is from a trusted source, click Enable Macros.
	  If you are not sure and want to prevent any macros from running, click
	  Disable Macros.
	
	CAUSE
	=====
	
	When you delete macros from a document or template, some macro storage
	components are left behind. The macro virus protection feature finds this
	information, and the warning message is displayed.
	
	WORKAROUND
	==========
	
	Use one of the following methods to create a new Word document that does not
	contain Word macro storage components.
	
	Method 1: Copy All Information to a New Word File
	-------------------------------------------------
	
	Create a new document or template and then copy all text, styles, AutoText
	entries, and so forth, but do not copy any macros to the new file. To create a
	new Word file, do one of the following:
	
	- Copy and paste the document to a new file. To do this, follow these steps:
	
	  1. Press CTRL+END to go to the bottom of your Word document.
	
	  2. Press CTRL+SHIFT+HOME to select everything from the end of the file to the
	     beginning of the file.
	
	  3. On the Edit menu, click Copy.
	
	  4. On the File menu, click New. On the General tab, click Blank Document, and
	     then click OK.
	
	  5. On the Edit menu, click Paste.
	
	  6. On the File menu, click Save As and save your new Word document with a new
	     file name.
	
	  -or-
	
	- Insert your file into a new Word document. To do this, follow these steps:
	
	  1. On the File menu, click New. On the General tab, click Blank Document, and
	     then click OK.
	
	  2. On the Insert menu, click File.
	
	  3. In the Insert File dialog box, select your problem file, and then click
	     OK.
	
	  4. On the File menu, click Save As and save your new Word document.
	
	  -or-
	
	- Create a new Word template from the problem template. To do this, follow
	  these steps:
	
	  1. On the File menu, click New.
	
	  2. Select your problem template. Under Create New, click Template, and then
	     click OK.
	
	  3. On the File menu, click Save As and save your new template.
	
	Method 2: Save the Word File as Rich Text Format (RTF)
	------------------------------------------------------
	
	1. Delete all the macros from the file.
	
	2. On the File menu, click Save As.
	
	3. In the Save As dialog box, under Save As Type, click Rich Text Format, and
	  then click OK.
	
	4. Close and then reopen the RTF file that you just saved.
	
	5. On the File menu, click Save As.
	
	6. In the Save As dialog box, in the Save as type box, click Word Document
	  (*.doc), and then click OK.
	
	7. Close and reopen the document. The macro storage components have been reset.
	
	The macro virus warning no longer appears when you open the document.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.
	
	MORE INFORMATION
	================
	
	Macro storage components are not present in a Word document or template until
	you store a macro in the file. These components exist as supporting structures
	for the existence and storage of macros in a file. When you delete all of the
	macros in a file, the macro storage components are not removed. The macro virus
	warning feature of Microsoft Word 97 detects the macro storage components in the
	file and presents the macro virus warning when you open the file.
	
	To remove macros from a Word document, do the following:
	
	1. Open the file in Word.
	
	2. On the Tools menu, point to Macro, and then click Macros.
	
	3. In the Macros dialog box, select a macro name, and then click Delete. This
	  removes the macro from the file.
	
	4. Repeat step 3 for each of the macros that you want to remove.
	
	To turn off macro virus protection, do the following:
	
	1. On the Tools menu, click Options, and then click the General tab.
	
	2. Clear the Macro Virus Protection check box, and then click OK.
	
	NOTE: Microsoft does not recommend that you disable the macro virus protection
	warning even if you have an updated macro virus protection software program
	installed on your system.
	
	Additional query words: prompt
	
	======================================================================
	Keywords          : kbdta word8 word97 kbfaq
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Issue type        : kbbug
	Solution Type     : kbnofix
	
	=============================================================================
	

{% endraw %}
