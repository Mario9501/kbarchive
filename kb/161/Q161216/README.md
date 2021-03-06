---
layout: page
title: "Q161216: SMS: Client Setup Fails to Update Sms.ini on Windows NT System"
permalink: /kb/161/Q161216/
---

## Q161216: SMS: Client Setup Fails to Update Sms.ini on Windows NT System

{% raw %}

	Article: Q161216
	Product(s): Microsoft Systems Management Server
	Version(s): 1.0,1.1,1.2
	Operating System(s): 
	Keyword(s): kbsetup kbInventory smssetup smsinv
	Last Modified: 20-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 1.0, 1.1, 1.2 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When the directory and file permissions are set to Read (RX) for the root of
	drive C on a computer running Windows NT, the Systems Management Server client
	setup program, Cli_nt.exe, cannot update the Sms.ini file. Even if the group
	"Everyone" is given full rights to the Sms.ini file, the file will not be
	updated. The following error message, indicating that Client Setup is unable to
	update the Sms.ini file, will be displayed when the application runs:
	
	  Problem opening or creating SMS.INI
	
	CAUSE
	=====
	
	Systems Management Server Client Setup attempts to create a temporary file in
	the root of drive C with a unique file name that is determined at the time of
	file creation. It will then write what will be the current contents of the
	Sms.ini file to this temporary file. Once this step has been completed, and no
	errors are detected, Client Setup will then copy the temporary file to Sms.ini,
	and then delete the temporary file.
	
	Because all standard user rights can be locked down in drive C (according to
	Windows NT security recommendations), the Systems Management Server inventory
	operation described above will fail while trying to create a new temporary file.
	
	WORKAROUND
	==========
	
	To work around this problem, provide 'Change (RWXD)' rights to the root of drive
	C.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	versions 1.0, 1.1 and 1.2. A supported fix is now available for version 1.2
	only, but has not been fully regression-tested and should be applied only to
	systems experiencing this specific problem. Unless you are severely impacted by
	this specific problem, Microsoft recommends that you wait for the next Service
	Pack that contains this fix. Contact Microsoft Technical Support for more
	information.
	
	
	MORE INFORMATION
	----------------
	
	The supported fix requires a new Cli_nt.exe file that exposes the temporary file
	name created during the Sms.ini update. The new file name is Sms.new. If this
	file does not exist, it will be created in the root of drive C. If it does
	already exist, it will be opened and truncated. After Sms.new is created or
	opened, the updated Sms.ini information is written to this file. When this
	operation is completed, the file is copied back to Sms.ini. This file is no
	longer be deleted, but flagged with the Hidden file attribute instead.
	
	Administrators can create a blank Sms.new file in a user's root directory, assign
	it the appropriate rights, and then lock down all other files except Sms.ini.
	This allows administrators to lock down the entire root directory on computer
	running Windows NT, except for the Sms.new and Sms.ini files, and the Systems
	Management Server inventory mechanism will continue to work properly.
	
	Additional query words: prodsms cli_nt rights
	
	======================================================================
	Keywords          : kbsetup kbInventory smssetup smsinv 
	Technology        : kbSMSSearch kbSMS100 kbSMS110 kbSMS120
	Version           : :1.0,1.1,1.2
	
	=============================================================================
	

{% endraw %}
