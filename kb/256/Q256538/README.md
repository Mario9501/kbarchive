---
layout: page
title: "Q256538: Creating an XML Page and Style Sheet to Display FoxPro Data"
permalink: /kb/256/Q256538/
---

## Q256538: Creating an XML Page and Style Sheet to Display FoxPro Data

{% raw %}

	Article: Q256538
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kbfile kbCtrl kbInternet kbvfp600 kbGrpDSFox kbGrpDSMDAC kbDSupport kbCodeSnippet kbMDA
	Last Modified: 04-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	FoxToXML.prg is a program file that creates a custom FoxPro class that uses a
	FoxPro cursor or table to create an eXtensible Markup Language (XML) page and an
	eXtensible Stylesheet Language (XSL) style sheet to display FoxPro data.
	
	The FoxPro class (FoxToXML) has a method that creates an XML file, a method that
	creates an XSL file, and a method that creates both files. Each method takes
	either no parameter and uses the currently open cursor or table to create the
	XML/XSL files or takes a table name as a parameter to create the files.
	
	The creation of the XML/XSL documents uses native Visual FoxPro 6.0 language and
	the custom class can be instantiated and used whenever an XML or XSL document is
	needed. The XML/XSL document names are derived from the cursor or table name.
	
	Without the XSL file, the XML data displays in hierarchical form. Create just an
	XML file and delete the "?xml-stylesheet ..." line to see how the XML data looks
	without the style sheet.
	
	MORE INFORMATION
	================
	
	The following file is available for download from the Microsoft Download
	Center:
	
	  FoxToXML.exe
	  (http://download.microsoft.com/download/vfox60/sample/11/w9x2k/en-us/FoxToXML.exe)
	
	Release Date: Mar-29-2000
	
	For additional information about how to download Microsoft Support files, click
	the following article number to view the article in the Microsoft Knowledge
	Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft scanned this file for viruses. Microsoft used the most current
	virus-detection software that was available on the date that the file was
	posted. The file is stored on secure servers that prevent any unauthorized
	changes to the file.
	
	The FoxToXML.EXE file contains the following files:
	
	+-----------------------+
	| Table Name   | Size   | 
	+-----------------------+
	| FoxToXML.PRG | 7.25KB | 
	+-----------------------+
	| FoxToXML.HTM | 1.95KB | 
	+-----------------------+
	
	FoxToXML.exe is a self-extracting zipped file that contains a Visual FoxPro 6.0
	program file and a readme file called FoxToXML.HTM.
	
	The FoxToXML program file contains code that creates a FoxPro custom class with
	three methods that create an XML file, an XSL file, or both files. Once the
	zipped files have been extracted, the XML and XSL files can be created as
	follows:
	
	1. Create a new program called "Test.prg" (without the quotation marks), and add
	  the following code:
	
	  CD JUSTPATH(SYS(16))
	  USE ? && Choose any FoxPro table
	  oXML = NEWOBJECT("FoxToXML","FoxToXML.PRG")
	  oXML.BOTH
	
	2. Save the program as TEST.PRG in the same directory as FoxToXML.PRG.
	
	3. Run TEST.PRG. This creates both an XML and XSL file with the name of the open
	  table or cursor.
	
	Alternatively, the following code creates an XML file with the name XYZ.XML (the
	name of the cursor):
	
	  SELECT * FROM tablename into CURSOR xyz
	  SET PROCEDURE TO FoxToXML.PRG
	  oXML = CREATEOBJECT("FoxToXML")
	  oXML.XML
	
	This code creates XML and XSL files in the default directory with the same name
	as the currently selected table or cursor. Double-click the XML file to display
	the FoxPro data in the default Internet browser.
	
	REFERENCES
	==========
	
	For more general information about XML, see the following Web sites:
	
	  HTTP://msdn.microsoft.com/xml
	
	  HTTP://www.xml.com
	
	Additional query words: FoxToXML
	
	======================================================================
	Keywords          : kbfile kbCtrl kbInternet kbvfp600 kbGrpDSFox kbGrpDSMDAC kbDSupport kbCodeSnippet kbMDAC260 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP600
	Version           : WINDOWS:6.0
	
	=============================================================================
	

{% endraw %}
