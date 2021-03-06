---
layout: page
title: "Q163160: WD97: Sample Macro to Remove a Submenu from a Menu"
permalink: /kb/163/Q163160/
---

## Q163160: WD97: Sample Macro to Remove a Submenu from a Menu

{% raw %}

	Article: Q163160
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbmacroexample word8 word97
	Last Modified: 13-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	
	SUMMARY
	=======
	
	This article provides a sample Visual Basic for Applications macro that removes
	a custom submenu from a custom menu.
	
	MORE INFORMATION
	================
	
	Microsoft provides programming examples for illustration only, without warranty
	either expressed or implied, including, but not limited to, the implied
	warranties of merchantability and/or fitness for a particular purpose. This
	article assumes that you are familiar with the programming language being
	demonstrated and the tools used to create and debug procedures. Microsoft
	support professionals can help explain the functionality of a particular
	procedure, but they will not modify these examples to provide added
	functionality or construct procedures to meet your specific needs. If you have
	limited programming experience, you may want to contact a Microsoft Certified
	Partner or the Microsoft fee-based consulting line at (800) 936-5200. For more
	information about Microsoft Certified Partners, please visit the following
	Microsoft Web site:
	
	  http://www.microsoft.com/partner/referral/
	
	For more information about the support options that are available and about how
	to contact Microsoft, visit the following Microsoft Web site:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	In Visual Basic for Applications, you can add or remove menus and submenus using
	the CommandBars collection. To remove a submenu, you must use an index in
	addition to the CommandBars collection. The index identifies the submenu using
	either a number or the menu name.
	
	     Public Sub RemoveSubMenu()
	
	        Dim objMenuBar As Object
	        ' Opens MyMenu which contains the submenu you want to remove.
	        Set objMenuBar = CommandBars.ActiveMenuBar. _
	           Controls("MyMenu").CommandBar
	        ' Removes MySubMenu.
	        objMenuBar.Controls("MySubMenu").Delete
	
	     End Sub
	
	For more information about using CommandBars, from the Visual Basic for
	Applications Editor, click the Office Assistant, type "CommandBars" (without the
	quotation marks), click Search, and then click to view "CommandBar Object."
	
	NOTE: If the Assistant is hidden, click the Office Assistant button on the
	Standard toolbar. If Visual Basic Help is not installed on your computer, please
	see the following article in the Microsoft Knowledge Base:
	
	  Q120802 Office: How to Add/Remove a Single Office Program or Component
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q173707 OFF97: How to Run Sample Code from Knowledge Base Articles
	
	
	Additional query words: wordcon vba vbe kbmacro
	
	======================================================================
	Keywords          : kbmacroexample word8 word97 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	
	=============================================================================
	

{% endraw %}
