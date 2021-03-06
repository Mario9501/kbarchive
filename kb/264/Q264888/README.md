---
layout: page
title: "Q264888: WD97: &quot;A Program Is Trying to Access ...&quot; Sending Mail Merge"
permalink: /kb/264/Q264888/
---

## Q264888: WD97: &quot;A Program Is Trying to Access ...&quot; Sending Mail Merge

{% raw %}

	Article: Q264888
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbdta kbmerge wd2000
	Last Modified: 14-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word for Windows 95 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you perform a mail merge in Microsoft Word 97 and send the results to
	electronic mail (e-mail), you receive the following warning:
	
	  A program is trying to access e-mail addresses you have stored in Outlook. Do
	  you want to allow this?
	
	  If this is unexpected, it may be a virus and you should choose "No".
	
	If you click Yes, you receive the following warning:
	
	  A program is trying to automatically send e-mail on your behalf. Do you want
	  to allow this?
	
	  If this is unexpected, it may be a virus and you should choose "No"."
	
	NOTE: This behavior occurs whether you are running Microsoft Outlook in Internet
	Mode Only (IMO) or in Corporate Workgroup (CW) mode.
	
	CAUSE
	=====
	
	This behavior occurs if you have installed the Outlook E-mail Security Update.
	The Outlook E-mail Security Update provides additional levels of protection
	against malicious e-mail messages. The update changes the way that Outlook
	handles attachments and the way that Outlook can be controlled
	programmatically.
	
	For additional information about this update, please see one of the following
	articles in the Microsoft Knowledge Base, depending on which version of Outlook
	you have:
	
	  Q262631 OL2000: Information About the Outlook E-mail Security Update
	
	  Q262617 OL98: Information About the Outlook E-mail Security Update
	
	This behavior of the Microsoft Word Mail Merge to E-mail feature is by design
	when the Outlook E-Mail Security Update is installed.
	
	MORE INFORMATION
	================
	
	The Word for Windows Mail Merge feature can output merged documents in the
	following formats:
	
	- Printer
	
	- New document
	
	- Electronic fax (if installed)
	
	- Electronic mail (if installed)
	
	REFERENCES
	==========
	
	For more information about the mail merge feature, click "Contents and Index" on
	the Help menu, click the Index tab in Word Help, type the following text
	
	  mail merge
	
	and then double-click the selected text to go to the "mail merge" topic. If you
	are unable to find the information you need, ask the Office Assistant.
	
	Additional query words: wd97 virusupdate virus patch
	
	======================================================================
	Keywords          : kbdta kbmerge wd2000 
	Technology        : kbWordSearch kbWord700Search
	Version           : WINDOWS:97
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
