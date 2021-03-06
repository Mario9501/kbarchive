---
layout: page
title: "Q255523: Permissions on Temp Folder Are Set Incorrectly with FlatTemp"
permalink: /kb/255/Q255523/
---

## Q255523: Permissions on Temp Folder Are Set Incorrectly with FlatTemp

{% raw %}

	Article: Q255523
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0 SP4,4.0 SP5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 4.0 SP4, 4.0 SP5, Terminal Server Edition 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After you run the "flattemp /enable" command on a Terminal Server with either
	Service Pack 4 or Service Pack 5 installed, the Temp folder permissions are
	changed when a user logs on to the Terminal Server console. The existing
	permissions are replaced with:
	
	  <Username> [FC]
	  Administrators [FC]
	  System [FC]
	
	The correct permissions for the Temp folder should be:
	
	  Creator Owner [FC]
	  Everyone [Change]
	  Administrators [FC]
	  System [FC]
	
	Attempting to access the Temp folder in a Terminal Server session results in an
	"Access denied" error message.
	
	CAUSE
	=====
	
	The local console logon process ignores the FlatTemp registry setting and sets
	the permissions on the Temporary folder to allow access only to the logged-on
	user.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem that is described in this article. Only apply it to systems
	that are experiencing this specific problem. This fix may receive additional
	testing. Therefore, if you are not severely affected by this problem, Microsoft
	recommends that you wait for the next Windows NT 4.0, Terminal Server Edition,
	service pack that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, visit the following Microsoft
	Web site:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are ordinarily incurred for support calls
	may be canceled if a Microsoft Support Professional determines that a specific
	update will resolve your problem. The usual support costs will apply to
	additional support questions and issues that do not qualify for the specific
	update in question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Date        Time     Size      File name    Platform
	  ----------------------------------------------------
	  02/11/2000  12:04p   207,120   Msgina.dll   Intel
	
	
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in the Microsoft products that
	are listed at the beginning of this article.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbNTTermServ400sp4 kbNTTermServ400sp5 kbNTTermServSearch
	Version           : winnt:4.0 SP4,4.0 SP5
	Hardware          : x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
