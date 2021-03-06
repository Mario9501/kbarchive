---
layout: page
title: "Q183215: WD97: Object Not a Collection Error in SynonymInfo.MeaningList"
permalink: /kb/183/Q183215/
---

## Q183215: WD97: Object Not a Collection Error in SynonymInfo.MeaningList

{% raw %}

	Article: Q183215
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbdta kbdtacode kbproof kbmacroexample word8 word97
	Last Modified: 13-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you use the Microsoft Visual Basic for Applications MeaningList property,
	you may receive the following error message:
	
	  Run-time error '451' Object not a collection.
	
	CAUSE
	=====
	
	You may be setting and using an object variable in conjuction with the
	MeaningList property as in the following example Visual Basic for Applications
	code,
	
	     Set oSynonymInfo = ActiveDocument.Content.SynonymInfo
	
	and then calling the property as follows:
	
	     Msgbox oSynonymInfo.MeaningList(1)
	
	Because Visual Basic for Applications treats the "(1)" in "MeaningList(1)" as a
	parameter being passed to MeaningList, rather than an index to the MeaningList
	array, the error described in the symptoms section of this article may occur.
	
	WORKAROUND
	==========
	
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
	
	To work around this problem, access the MeaningList array directly without first
	setting it to a variable. The following two examples successfully use the
	MeaningList property to return the meaning of a word from the thesaurus.
	
	Example 1
	---------
	
	The following sample macro allows you to index the array:
	
	     The following sample macro allows you to index the array:
	
	     Sub TellMeaning()
	        'Insert a word into the active document
	        ' removing all other text.
	        ActiveDocument.Content.Text = "pretty"
	
	        'Displays the first meaning of the word in the document.
	        MsgBox ActiveDocument.Content.SynonymInfo.MeaningList(1)
	     End Sub
	
	Example 2
	---------
	
	The following sample macro returns the first synonym for the selected text and
	traps the error if the word has no definition in the thesaurus.
	
	     Sub TellMeaning()
	
	        On Error Resume Next
	        ' Displays the first meaning of the word in the document.
	        MsgBox Selection.Range.SynonymInfo.MeaningList(1)
	
	        ' Check for likely automation errors.
	        If Err.Number = 9 Then  'SUBSCRIPT OUT OF RANGE
	           ' Tell user what happened. Then clear the Err object.
	           MsgBox "No Definition"
	           Err.Clear   ' Clear Err object fields.
	        End If
	
	     End Sub
	
	For more information about the MeaningList property, from the Visual Basic
	Editor, click the Office Assistant, type "MeaningList" (without the quotation
	marks), click Search, and then click to view "MeaningList Property."
	
	NOTE: If the Assistant is hidden, click the Office Assistant button on the
	Standard toolbar. If the Assistant is not able to answer your query, please see
	the following article in the Microsoft Knowledge Base:
	
	  Q176476 OFF: Office Assistant Not Answering Visual Basic Questions
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products listed at
	the beginning of this article.
	
	MORE INFORMATION
	================
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q173707 OFF97: How to Run Sample Code from Knowledge Base Articles
	
	
	REFERENCES
	==========
	
	For more information about getting help with Visual Basic for Applications,
	please see the following article in the Microsoft Knowledge Base:
	
	  Q163435 VBA: Programming Resources for Visual Basic for Applications
	
	Additional query words: wordcon vb vba vbe
	
	======================================================================
	Keywords          : kbdta kbdtacode kbproof kbmacroexample word8 word97 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
