---
layout: page
title: "Q295450: SMS:  SMS Status Manager Reports 1215 Error Messages"
permalink: /kb/295/Q295450/
---

## Q295450: SMS:  SMS Status Manager Reports 1215 Error Messages

{% raw %}

	Article: Q295450
	Product(s): Microsoft Systems Management Server
	Version(s): 2.0 SP2,2.0 SP3
	Operating System(s): 
	Keyword(s): kberrmsg kbtool kbClient kbConfig kbMMC kbServer kbsms200 kbsms200bug kbStatSum
	Last Modified: 11-APR-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 2.0 SP2, 2.0 SP3 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After the weekend of April 1, 2001 (when we changed to daylight savings time),
	if you run the netsend command from the SMS status filter rules, warning
	messages may be displayed on the Systems Management Server (SMS) Administrator
	console. These messages state that a problem is reported from the Status Manager
	component.
	
	When you check the Status Manager component status messages, you see that
	multiple entries are generated that are similar to the following message:
	
	  1215 SMS Status Manager received a status message reported by component
	  "Hardware Inventory Agent" running on computer "COMPUTER1", and the time
	  stamp on the message is more recent than the current system time on the site
	  server.
	
	  Possible cause: The system clock on computer "COMPUTER1" is 3575 or more
	  seconds ahead of the site server's system clock. Solution: Synchronize the
	  system clock of computer "COMPUTER1" with the site server's system clock.
	  Please refer to your Windows NT Server documentation or the Microsoft
	  Knowledge Base for further information.
	
	  SMS Status Manager will process status messages with improper time stamps when
	  the site server's system clock surpasses the improper time stamps. For
	  example, this status message will not be processed for 3575 seconds. SMS
	  Status Manager will continue to report this problem every 24 hours until you
	  fix it.
	
	  SMS Status Manager will not report this problem if the system clock of
	  computer "COMPUTER1" is less than 300 seconds ahead of the site server's
	  system clock. This interval is configurable in the SMS site control file.
	  Please refer to the Microsoft Knowledge Base for further information.
	
	CAUSE
	=====
	
	This issue occurs because in SMS Service Pack 2 (SP2), the hardware inventory
	component is moved to its own process (its own service). The new service-based
	implementation of the SMS Hardware Inventory Agent uses a statically linked
	version of the C runtime library that incorrectly calculates time for the first
	week of daylight savings time.
	
	For additional information about this behavior, click the article number below to
	view the article in the Microsoft Knowledge Base:
	
	  Q214661 FIX: Daylight Savings Time Bug in C Run-Time Library
	
	When the Hardware Inventory Agent completes an inventory cycle, it creates a
	status message that contains the incorrect time, and then forwards it to the SMS
	site server. Status Manager on the SMS site server evaluates the timestamp on
	the status message file (.svf), and notices that the time is more recent than
	the current server time. Status Manager moves this file to
	Sms\Inboxes\Statmgr.box\Futureq so that it can process it at a later time, and
	then generates the warning message described in the preceding section.
	
	NOTE: This behavior only occurs when the computer is using this particular
	runtime library when the transition date (the day we change to Daylight Savings
	Time) falls on the first day of the month.
	
	WORKAROUND
	==========
	
	To work around this issue, create a new status filter rule to prevent "1215"
	status messages from being forwarded to the Status Summarizers.
	
	To create a new status filter rule:
	
	1. In the SMS Administrator console, locate and click the following node:
	
	  
	
	  Site Database
		|
		-<site code - site name>
			|
			- Site Settings
				|
				- Status Filter Rules
	
	2. On the Action menu, click New, and then click Status Filter Rule.
	
	3. Click the General tab, and then type a status filter rule name in the Name
	  box, for example "NO1215" (without the quotation marks).
	
	4. Click Component, and then type "SMS_Status_Manager" (without the quotation
	  marks).
	
	5. Click MessageID, and then type "1215" (without the quotation marks).
	
	6. Click the Actions tab, and then click to select the "Do Not Forward to Status
	  Summarizers" check box.
	
	7. Increase the priority of the new filter:
	
	  a. Expand the Status Filter Rules node.
	
	  b. Right-click the new NO1215 rule, and then click Increment Priority.
	
	  c. Repeat these steps until this status filter rule is displayed at the top
	     of the list.
	
	When you complete this procedure to increase the priority of the filter, the
	components are prevented from going into a warning or critical state. However,
	this procedure does not stop the messages from being loaded into the SMS site
	database or being viewed by Status Message Viewer.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	version 2.0.
	
	MORE INFORMATION
	================
	
	This problem stops occurring one week after the transition to daylight savings
	time.
	
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kberrmsg kbtool kbClient kbConfig kbMMC kbServer kbsms200 kbsms200bug kbStatSum 
	Technology        : kbSMSSearch kbSMS200SP2 kbSMS200SP3
	Version           : :2.0 SP2,2.0 SP3
	Issue type        : kbbug
	Solution Type     : kbnofix
	
	=============================================================================
	

{% endraw %}
