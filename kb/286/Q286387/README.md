---
layout: page
title: "Q286387: SMS: Software Inventory Doesn't Update SMS Database"
permalink: /kb/286/Q286387/
---

## Q286387: SMS: Software Inventory Doesn't Update SMS Database

{% raw %}

	Article: Q286387
	Product(s): Microsoft Systems Management Server
	Version(s): 1.2 SP4
	Operating System(s): 
	Keyword(s): kberrmsg kbtool kbConfig kbMMC kbsms120 kbInventory kbMaintMan kbPackage kbsmsAdmin kbS
	Last Modified: 26-APR-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 1.2 SP4 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Although a package is delivered to client computers and inventory collection is
	enabled, Software Inventory information is not updated on the SMS database. In
	the Maintman.log file on the site server, which is located in \SMS\logs\ folder,
	may have the following error message logged:
	
	  ERROR in Package rule file: syntax error Line: 1~~
	
	CAUSE
	=====
	
	This behavior occurs because when an SMS 1.2 client logs on to the domain, it
	checks the Pkg_16.cfg file in the \SMS\Logon.srv file. If Pkg_16.cfg is a zero
	byte file, the client does not have the necessary information regarding what to
	collect for the software inventory. This behavior can occur when the Package.rul
	file, that is located in \SMS\Site.srv\Maincfg.box\Pkgrule folder contains a
	negative CHECKSUM value.
	
	For example,
	
	  PACKAGE 58 "Captura Submitter 4.09" FILE "submit4.EXE" DATE 12/28/00 BYTE 0
	  77 CHECKSUM 0 0 -1830212815
	  PACKAGE 59 "Captura v4.09M (Build 827) Full" FILE "captura4.EXE" DATE 01/04/01
	  BYTE 0 77 CHECKSUM 0 0 -1742860494
	
	WORKAROUND
	==========
	
	To work around this behavior, you have to eliminate the negative CHECKSUM value.
	To do so, use either of the following methods:
	
	Method 1
	--------
	
	1. Open Package.rul in \SMS\Site.srv\Maincfg.box\Pkgrule\ by using Notepad.exe.
	
	2. Delete the lines that have a negative CHECKSUM value.
	
	3. Stop, and then restart SMS_Maintenance_Manager. To do this, go in the SMS
	  Administrator Program, and then on the Tool menu, click SMS Service Manager.
	
	4. Verify that the Pkg_16.cfg file is not a zero byte file.
	
	Method 2
	--------
	
	To delete the package that is causing the zero byte Pkg_16.cfg file:
	
	1. In the SMS Administrator console, click the Package icon, and then locate the
	  package.
	
	2. Create a Remove Package from Server job.
	
	3. After the job deletes packages from distribution servers, delete the package.
	
	4. Stop and then restart SMS_Maintenance_Manager.
	
	5. Verify that the Pkg_16.cfg file is not a zero byte file.
	
	MORE INFORMATION
	================
	
	Application Manager monitors the SMS database for new or changed inventory
	packages and creates a file that is called an inventory rule file (Package.rul).
	This file contains all of the defined inventory packages.
	
	Maintenance Manager copies a binary version of the inventory rule file
	(Package.rul) to all logon servers at the site.
	
	When you create a package, the file name, byte size, and CHECKSUM size can be
	added or retrieved. In some circumstances, a negative CHECKSUM value has been
	added even if the CHECKSUM field does not allow a negative value entry. If this
	is the case, the contents of Package.rul are created with a negative CHECKSUM
	value.
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kberrmsg kbtool kbConfig kbMMC kbsms120 kbInventory kbMaintMan kbPackage kbsmsAdmin kbSoftwareDist 
	Technology        : kbSMSSearch kbSMS120SP4
	Version           : :1.2 SP4
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
