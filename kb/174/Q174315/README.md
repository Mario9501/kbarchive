---
layout: page
title: "Q174315: WD97: Warning When You Save Multilingual Web Page or HTML File"
permalink: /kb/174/Q174315/
---

## Q174315: WD97: Warning When You Save Multilingual Web Page or HTML File

{% raw %}

	Article: Q174315
	Product(s): Word 97 for Windows
	Version(s): 
	Operating System(s): 
	Keyword(s): kbdta word8 word97 kbwdinternet
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	- the operating system: Microsoft Windows 2000 
	- the operating system: Microsoft Windows NT 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	In Microsoft Word 97, when you save a document as Hypertext Markup Language
	(HTML) or when you save a new Web page, you may receive the following warning
	message:
	
	  This document contains characters that are not in the current language
	  encoding. To preserve them, choose cancel and select the appropriate language
	  encoding. For multilingual documents, use UTF-8.
	
	CAUSE
	=====
	
	This message appears when your document contains multiple languages. The Word
	HTML converter cannot set the correct character set (language encoding) for the
	document.
	
	RESOLUTION
	==========
	
	To correct this problem, follow these steps:
	
	1. When you get the warning message described in the "Symptoms" section of this
	  article, click OK.
	
	2. On the File menu, click Properties.
	
	3. In the Document Properties dialog box, under "For Saving This Page", click to
	  select the correct language set that your document contains, and then click
	  OK.
	
	  For example:
	
	   - When your document contains English and Polish, select Central European.
	
	     -or-
	
	   - When your document contains English and Russian, select Cyrillic.
	
	4. On the File menu, click Save.
	
	This sets the language encoding of the document.
	
	If You Have a Problem Completing the Resolution
	-----------------------------------------------
	
	To set the correct language encoding, your Word document must be saved in the
	HTML file format before you click Properties on the File menu.
	
	To save as HTML, do one of the following:
	
	- On the File menu, click "Save as HTML".
	
	  -or-
	
	- On the File menu, click Save As. In the Save As dialog box, change the "Save
	  as type" box to HTML Document, and then click OK.
	
	If the Document Properties dialog box containing the option "For saving this
	page" is not displayed when you click Properties on the File menu, or if you are
	unable to save as HTML, Word may be experiencing any of the following problems:
	
	- "Save as HTML" missing on the File menu
	
	- HTML Document missing in the "Save as type" box (on the File menu, click Save
	  As)
	
	- Damaged or missing Windows Registry settings
	
	- Damaged or missing program files or components
	
	To resolve these problems, use one or more of the following methods:
	
	Method 1: Reinstall Microsoft Word:
	
	To reinstall Microsoft Word, follow these steps:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click Add/Remove Programs. In the list of installed programs, click
	  Microsoft Office 97 (Microsoft Word 97), and then click Add/Remove (on
	  Microsoft Windows 2000, click Change/Remove). If you installed Microsoft
	  Office from a CD, you are prompted to insert the first CD.
	
	3. If a dialog box displays a message that states that programs are running,
	  quit the programs, and then click OK.
	
	4. In the Microsoft Office 97 Setup dialog box, click Reinstall.
	
	Method 2: Run Setup with the /y Switch to Correct the Registry:
	
	Setup /y is a switch used by Office Setup and Office program Setup files. It
	allows a reinstallation of Office without performing file checks or actually
	reinstalling the files. Setup /y re-registers all Office components and returns
	the settings to their default values in the registry.
	
	To resolve this problem, try running Setup /y for Word or Office to repair
	registry corruption.
	
	To run Setup with the /y switch, follow these steps:
	
	1. Insert the Microsoft Word or Microsoft Office CD-ROM. If you installed Word
	  or Office from floppy disks, insert the Setup Disk 1 in your computer's
	  floppy disk drive.
	
	2. Click Start, and then click Run.
	
	3. In the Open box, type the following, and then click OK:
	
	  "<drive>:\setup.exe /Y" (without the quotation marks)
	
	  where <drive> is the letter of the drive that contains the CD or Setup
	  Disk 1.
	
	4. Click Reinstall.
	
	Method 3: Completely Remove Word and Reinstall:
	
	To completely remove Microsoft Word and reinstall, follow these steps:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click Add/Remove Programs. In the list of installed programs, click
	  Microsoft Office 97 (Microsoft Word 97), and then click Add/Remove (on
	  Microsoft Windows 2000, click Change/Remove). If you installed Microsoft
	  Office from a CD, you are prompted to insert the first CD.
	
	3. If a dialog box displays a message that states that programs are running,
	  quit the programs, and then click OK.
	
	4. In the Microsoft Office 97 Setup dialog box, click Remove All.
	
	5. Run the Eraser 97 utility to remove all remaining Office/Word files and to
	  delete corresponding registry entries.
	
	For additional information about the Office 97 File and Registry Eraser utility,
	click the article number below to view the article in the Microsoft Knowledge
	Base:
	
	  Q176823 OFF97: Utility to Completely Remove Remaining Office 97 Files
	
	6. When you are prompted to remove shared components, click Remove All.
	
	7. If you are prompted to restart the computer after Setup is completed, restart
	  the computer.
	
	8. Re-install either Microsoft Word 97 or Microsoft Office 97 for Windows.
	
	MORE INFORMATION
	================
	
	When you save your Web page in Word, the HTML converter writes the language
	encoding of the document similar to the following:
	
	  <META HTTP-EQUIV="Content-Type" CONTENT="text/html;
	  charset=windows-1252">
	
	When your document contains text typed in a different language in addition to
	English, the document may show incorrect characters when viewed in a Web
	browser.
	
	To correctly show text typed in a different language, the document language
	encoding must be set to the language typed. If your document contains text typed
	in a different language in addition to English, you must specify the specific
	language encoding of the additional language.
	
	REFERENCES
	==========
	
	For additional information, click the article numbers below to view the articles
	in the Microsoft Knowledge Base:
	
	  Q141306 How to Enable Support for Multiple Languages in Windows
	
	  Q150620 Error Message When You Change the Default Language
	
	
	  Q159950 WD97: General Information About International Functionality
	
	  Q183857 WD97: Save As HTML Command Missing from File Menu
	
	  Q170937 WD97: Supplemental Converter Not Listed in Files Of Type List
	
	Additional query words: 8.0 8.00 multi-lingual multi-language foreign other
	
	======================================================================
	Keywords          : kbdta word8 word97 kbwdinternet 
	Technology        : kbOSWin2000 kbWordSearch kbOSWinSearch kbWord97 kbWord97Search kbZNotKeyword2 kbOSWinNTSearch
	Version           : :
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
