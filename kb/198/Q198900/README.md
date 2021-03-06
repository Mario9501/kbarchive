---
layout: page
title: "Q198900: SMS: Access Violation Opening Script from Newer Version"
permalink: /kb/198/Q198900/
---

## Q198900: SMS: Access Violation Opening Script from Newer Version

{% raw %}

	Article: Q198900
	Product(s): Microsoft Systems Management Server
	Version(s): WINDOWS:1.0,2.0; winnt:1.2,2.0
	Operating System(s): 
	Keyword(s): kbsms200 kbsms200bug kbsms120 kbsms120bug kbsmsInst
	Last Modified: 11-JUL-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 2.0, 1.2 
	- Microsoft Systems Management Server Installer versions 1.0, 2.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When using an older version of Systems Management Server Installer to open a
	script (.ipf) file that was created with version 2.0.64.00 of the Installer, you
	may receive the following error:
	
	  SMSINS32.EXE - Application Error
	
	  The instruction at "0xXXXXXXXX" referenced memory at "0xXXXXXXXX". The memory
	  could not be "read".
	
	  Click on OK to terminate the application.
	  Click on Cancel to debug the application.
	
	To work around this problem, use the version of Systems Management Server
	Installer that was last used to save the Installer script to open the script
	(.ipf) file.
	
	CAUSE
	=====
	
	Script files (.ipf files) created with Systems Management Server Installer
	version 2.0.64.00 cannot be opened correctly with older versions of the
	Installer.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	Installer version 1.0 and 2.0 and Systems Mangement Server versions 1.2 and
	2.0.3 This problem has been corrected in the latest U.S. service pack for
	version 2.0. For information on obtaining the service pack, query on the
	following word in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	MORE INFORMATION
	================
	
	Version 2.0.64.00 of Systems Management Server is provided with Systems
	Management Server 2.0.
	
	Additional query words: prodsms smsinst Dr Watson drwatson doctor
	
	======================================================================
	Keywords          : kbsms200 kbsms200bug kbsms120 kbsms120bug kbsmsInst 
	Technology        : kbSMSSearch kbSMS120 kbSMS200 kbSMSI100 kbSMSI200
	Version           : WINDOWS:1.0,2.0; winnt:1.2,2.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
