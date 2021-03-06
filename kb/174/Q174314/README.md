---
layout: page
title: "Q174314: WD97: Cannot Copy from Word and Paste to GroupWise 4.1a"
permalink: /kb/174/Q174314/
---

## Q174314: WD97: Cannot Copy from Word and Paste to GroupWise 4.1a

{% raw %}

	Article: Q174314
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kb3rdparty winword word97
	Last Modified: 14-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you copy text in Microsoft Word 97 and paste to Novell GroupWise version
	4.1a, nothing appears in GroupWise.
	
	NOTE: You are able to copy text from GroupWise 4.1a and paste to Word 97. You are
	also able to copy text from other programs and paste to GroupWise 4.1a.
	
	
	RESOLUTION
	==========
	
	To resolve this problem, upgrade to GroupWise 5.1 32-bit client.
	
	To work around this problem, use either of the following methods.
	
	Method 1: Use NotePad
	---------------------
	
	1. In Word 97, copy your text and paste it into NotePad.
	
	2. In NotePad, do one of the following:
	
	   - Copy the text and then paste it into GroupWise.
	
	  -or-
	
	   - Save the text as a .txt file, and then use Import Documents in GroupWise
	     to open your document.
	
	Method 2: Use Word
	------------------
	
	1. Obtain and install the supplemental file converter for Word 6.0 for MS- DOS.
	
	2. In Word 97, click Save As on the File menu.
	
	3. Type a name for your document, and in the Save As Type list, click "Word 6.0
	  for Dos (*.doc)."
	
	4. In GroupWise, use the Import Documents command to open your document.
	
	For additional information about file converters, click the article numbers below
	to view the articles in the Microsoft Knowledge Base:
	
	  Q212265 WD: Additional Text Converters and Image Filters Available in
	  Microsoft Office Converter Pack
	
	  Q162987 WD97: Supported Non-Word File Formats
	
	STATUS
	======
	
	This problem no longer occurs with Novell GroupWise 5.1 or later.
	
	MORE INFORMATION
	================
	
	Novell GroupWise is a Document Management System (DMS) that uses Open Document
	Management API (ODMA). For more information about ODMA, please see the following
	article in the Microsoft Knowledge Base:
	
	  Q159963 WD97: Word 97 Supports ODMA
	
	Novell has confirmed that this problem occurs when you copy text from Word 97 and
	paste to GroupWise. For more information about this problem, please contact
	Novell.
	
	
	For additional information about how to contact Novell, please see the following
	article in the Microsoft Knowledge Base:
	
	  Q60781 Hardware and Software Third-Party Vendor Contact List, L-P
	
	GroupWise is manufactured by Novell, a vendor independent of Microsoft; we make
	no warranty, implied or otherwise, regarding this product's performance or
	reliability.
	
	Additional query words: 8.0 8.00
	
	======================================================================
	Keywords          : kb3rdparty winword word97 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Issue type        : kbhowto kbprb
	
	=============================================================================
	

{% endraw %}
