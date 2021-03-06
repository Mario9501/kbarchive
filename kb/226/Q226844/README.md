---
layout: page
title: "Q226844: SMS: Can't Enforce Security by Group with Sofware Metering"
permalink: /kb/226/Q226844/
---

## Q226844: SMS: Can't Enforce Security by Group with Sofware Metering

{% raw %}

	Article: Q226844
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:2.0,2.0 SP1,2.0 SP2
	Operating System(s): 
	Keyword(s): kbsms200 kbsms200bug kbsmsMeter
	Last Modified: 22-OCT-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 2.0, 2.0 SP1, 2.0 SP2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	An online client is unable to determine the groups that a user belongs to, and
	is therefore unable to enforce security by group. This failure to identify and
	apply the permissions to a specified group causes all members of the domain to
	be denied the product or products that are restricted by group.
	
	WORKAROUND
	==========
	
	Running Restricted Products on Clients That Have Permission
	-----------------------------------------------------------
	
	Modify the Software Metering Service account so that it specifies a qualified
	domain user account and adds the user account to the domain administrator's
	group; to do so, follow these steps:
	
	1. Navigate to Site Systems.
	
	2. Right-click the site system whose Software Metering Service account you want
	  to change, and then click Properties.
	
	3. In the Site System Properties dialog box, click the Software Metering Server
	  tab, and then click Set.
	
	4. In the Windows NT Account dialog box, specify an account of the form
	  domain\account.
	
	5. Click OK in all open dialog boxes.
	
	6. Wait until the next Software Metering server configuration cycle completes;
	  open User Manager for Domains to ensure that the account has been created. If
	  this is a new server installation, it requires two cycles to complete the
	  service account installation as a domain account.
	
	7. Add the newly created domain account to the domain administrator's group
	  using User Manager for Domains.
	
	8. If you are modifying the Software Metering Service account to resolve the
	  issue after the Software Metering server has been installed, you must stop
	  and restart the SMS_LICENSE_SERVER service (use the Services icon in Control
	  Panel) on the Software Metering server so that it uses the new account.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	version 2.0.
	
	MORE INFORMATION
	================
	
	NOTE: This behavior does not affect User and machine permissions.
	
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbsms200 kbsms200bug kbsmsMeter 
	Technology        : kbSMSSearch kbSMS200 kbSMS200SP1 kbSMS200SP2
	Version           : winnt:2.0,2.0 SP1,2.0 SP2
	Issue type        : kbbug
	Solution Type     : kbnofix
	
	=============================================================================
	

{% endraw %}
