---
layout: page
title: "Q184324: XWEB: Customizing the Checkname Feature for Outlook Web Access"
permalink: /kb/184/Q184324/
---

## Q184324: XWEB: Customizing the Checkname Feature for Outlook Web Access

{% raw %}

	Article: Q184324
	Product(s): Microsoft Exchange
	Version(s): WINDOWS:5.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 22-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Outlook Web Access, version 5.5 Service Pack 1 
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	In Exchange Server 5.5 Service Pack 1, the Outlook Web Access (OWA) client
	allows you to check and resolve names for e-mail recipients.
	
	You can control the maximum number of names displayed and the total lines of
	recipients displayed when resolving a name. This is handled through the
	following settings in the file Constant.inc located in the
	C:\Exchsrvr\Webdata\<lang> directory:
	
	  iCNMaxResolveNames = 10  {default setting}
	  iCNMaxLines        = 100 {default setting}
	
	MORE INFORMATION
	================
	
	If your Global Address List contains many variations of common names such as
	John or Susan, you may want to increase the value for iCNMaxResolveNames.
	Otherwise, you may receive the following message when you attempt to resolve the
	name with the OWA client:
	
	  Too many matches for Susan (11 found)
	  Ignore this recipient
	  Delete this recipient
	
	The reason you are receiving this message is because the client located 11
	instances of the name Susan. However, the default setting for Maximum Number of
	Resolved Names displayed is set to 10.
	
	If you receive the following message, you may have the ICNMaxLines set too low
	and OWA cannot display all the variations of the multiple recipients found:
	
	  Due to limits on the size of this dialog, 1 recipients could not be shown.
	  Resolve the recipients shown above, then press Check Names again to complete
	  the resolution of ambiguous recipients.
	
	NOTE: Included in the total number of lines displayed are the two lines that
	display the "Ignore this recipient" and "Delete this recipient" messages.
	
	======================================================================
	Keywords          :  
	Technology        : kbOutlookSearch kbOWASearch kbOWA550SP1
	Version           : WINDOWS:5.5
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
