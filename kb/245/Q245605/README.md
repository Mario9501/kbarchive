---
layout: page
title: "Q245605: Clusdisk.sys May Corrupt Pool Memory"
permalink: /kb/245/Q245605/
---

## Q245605: Clusdisk.sys May Corrupt Pool Memory

{% raw %}

	Article: Q245605
	Product(s): Microsoft Windows NT
	Version(s): 4.0,4.0 SP4,4.0 SP5,4.0 SP6
	Operating System(s): 
	Keyword(s): kbWinNT400PreSP7Fix
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server, Enterprise Edition versions 4.0, 4.0 SP4, 4.0 SP5, 4.0 SP6 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Clusdisk.sys may corrupt pool memory if you are running Microsoft Cluster Server
	with special pool overrun protection enabled for all tags. When this happens you
	may receive a "Stop 0x00000050" error message on boot. For additional
	information about enabling pool overrun protection, click the article number
	below to view the article in the Microsoft Knowledge Base:
	
	  Q192486 Introduction to Windows NT Kernel Special Pool
	
	CAUSE
	=====
	
	This behavior occurs when Clusdisk.sys attempts to write past its allocation
	memory.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem.
	
	To resolve this problem, contact Microsoft Product Support Services to obtain the
	fix. For a complete list of Microsoft Product Support Services phone numbers and
	information on support costs, please go to the following address on the World
	Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English-language version of this fix should have the following file
	attributes or later:
	
	  Date       Time      Size    File name      Platform
	  ----------------------------------------------------
	  11/05/99   4:38 PM   28 KB   Clusdisk.sys   Intel
	  11/05/99   4:37 PM   47 KB   Clusdisk.sys   Alpha
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbWinNT400PreSP7Fix 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400sp6 kbWinNTSEnt400sp5 kbWinNTSEnt400sp4 kbWinNTSEnt400 kbWinNTS400search
	Version           : :4.0,4.0 SP4,4.0 SP5,4.0 SP6
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
