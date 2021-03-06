---
layout: page
title: "Q263691: Environment Variables in TrustedDriverPath Are Not Resolved"
permalink: /kb/263/Q263691/
---

## Q263691: Environment Variables in TrustedDriverPath Are Not Resolved

{% raw %}

	Article: Q263691
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0 SP5,4.0 SP6
	Operating System(s): 
	Keyword(s): kbenv
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 4.0 SP5, 4.0 SP6, Terminal Server Edition 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Drivers may not be copied from the trusted drivers path. Instead, you may be
	prompted to insert a CD-ROM.
	
	CAUSE
	=====
	
	This problem can occur if the following registry key is set to
	%SystemRoot%\system32\spool\drivers\w32%PROCESSOR_ARCHITECTURE%:
	
	  HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Print\Providers\LanMan
	  Print Services\Servers\TrustedDriverPath
	
	Because of this, the variables are not resolved, and the drivers are not copied
	from the TrustedDriverPath.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem. This fix may receive additional
	testing at a later time, to further ensure product quality. Therefore, if you
	are not severely affected by this problem, Microsoft recommends that you wait
	for the next Windows NT 4.0 service pack that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Date      Time                 Size    File name     Platform
	  -------------------------------------------------------------
	  05/31/2000  06:02p             164,112 Win32spl.dll  Alpha
	  05/31/2000  06:17p              80,144 Win32spl.dll  Intel
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT 4.0.
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbenv 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbNTTermServ400sp5 kbNTTermServ400sp6 kbNTTermServSearch
	Version           : winnt:4.0 SP5,4.0 SP6
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
