---
layout: page
title: "Q174463: Reduce Potential Problems Performing WinNT 3.51 to 4.0 Upgrade"
permalink: /kb/174/Q174463/
---

## Q174463: Reduce Potential Problems Performing WinNT 3.51 to 4.0 Upgrade

{% raw %}

	Article: Q174463
	Product(s): Microsoft Windows NT
	Version(s): WinNT:3.51,4.0
	Operating System(s): 
	Keyword(s): kbsetup kbhowto
	Last Modified: 10-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 3.51, 4.0 
	- Microsoft Windows NT Server versions 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article is designed to help users prepare for, and complete a successful
	upgrade from Windows NT 3.51 to Windows NT 4.0. In most cases, the upgrade
	process will complete successfully without additional steps. However, these
	extra measures can aid in assuring the upgrade goes smoothly.
	
	MORE INFORMATION
	================
	
	Upgrade Preparation
	-------------------
	
	1. Check to see if your system's hardware (including all additional components)
	  is on the Windows NT 4.0 Hardware Compatibility List (HCL). Obtain Windows NT
	  4.0 drivers from vendors of non-HCL equipment. See the More Information about
	  Third-Party Drivers section below for additional information regarding
	  non-HCL systems, components, and drivers.
	
	2. Perform a full backup of all drives including the system's local registry.
	
	3. Update your Emergency Repair Disk (ERD) using the Rdisk.exe command at an
	  MS-DOS prompt or by double-clicking Rdisk.exe in Windows NT Explorer.
	
	4. If the partition where Windows NT is installed (usually drive C), is mirrored
	  using Windows NT software fault tolerance, break the mirror using Disk
	  Administrator.
	
	5. If the system contains any other software and fault tolerance sets (mirror,
	  stripe set, stripe set with parity, volume set), backup the disk
	  configuration from Disk Administrator.
	
	  In Disk Administrator, click Partition, point to Configuration, and then click
	  Save. This will save your configuration to floppy disk.
	
	6. Identify all third-party services and devices. Look in the Control Panel
	  Services tool and Control Panel Devices tool. Confirm Windows NT 4.0
	  compatibility with the vendors of the identified drivers and services.
	  Upgrade or disable drivers or services not compatible with Windows NT 4.0.
	  See the "More Information about Third-Party Drivers" section below for
	  additional information.
	
	  It is also a good idea to disable any non-essential services prior to the
	  upgrade. For example, virus-scanning software, backup software, Compaq's
	  Insight manager, and so forth.
	
	  To disable services, start the Control Panel Services tool. Note the current
	  Startup settings by selecting the service, then selecting Startup. Document
	  the current setting for later use. Then set the startup to Manual. Stop the
	  service. If unable to stop the service, restart the system. Because the
	  startup is now set for Manual the service will not start.
	
	7. Run CHKDSK from an MS-DOS command prompt on the system or boot drive, usually
	  drive C.
	
	Perform the Upgrade
	-------------------
	
	If the upgrade is successful, install any required third-party drivers or
	services. Enable any services disabled in step 6 above that where not enabled by
	installing a newer version. Be sure to set the Startup setting in the Control
	Panel Services tool to the setting found during step 6.
	
	More Information about Third-Party Drivers
	------------------------------------------
	
	A common cause of upgrade failure is incompatibility with third-party drivers or
	services. Windows NT will automatically replace any of the Windows NT 3.51
	native drivers with the Windows NT 4.0 version during the upgrade. If the
	drivers are supplied by a third-party vendor, there may not be a Windows NT 4.0
	version on the Windows NT CD. For this reason, it is important to identify
	third-party drivers and update or disable them prior to the upgrade. Also, be
	aware that some drivers are Windows NT 3.51 or Windows NT 4.0 specific. In these
	cases, disabling the service or uninstalling the driver prior to the upgrade is
	the safest route. After the Windows NT 4.0 upgrade is complete, install the
	Windows NT 4.0 version of the driver or service. For examples of upgrade failure
	because of third- party drivers see the following articles in the Microsoft
	Knowledge Base:
	
	ARTICLE-ID: Q172229
	TITLE : Stop 0x00000050 During WinNT 3.51 to 4.0 Upgrade on Compaq
	
	ARTICLE-ID: Q171317
	TITLE : Upgrade WinNT to 4.0 May Hang with Trident 94XX AGI Video Card
	
	ARTICLE-ID: Q158272
	TITLE : Printer Disappears After Upgrading to Windows NT 4.0
	
	Information on Non-HCL Hardware, Components, and Software
	---------------------------------------------------------
	
	If your system has been running as expected with Windows NT 3.51 that is no
	guarantee that Windows NT 4.0 will install and run properly. To test Windows NT
	4.0 on your specific hardware, you may want to perform a new Windows NT 4.0
	installation into a different directory on the same system, before committing
	your Windows NT 3.51 installation. If the Windows NT 4.0 installation was
	successful, install the third-party drivers and services to verify they will
	work with Windows NT 4.0.
	
	For more information on the Microsoft Hardware Compatibility List, please see the
	following Microsoft Knowledge Base articles:
	
	ARTICLE-ID: Q142865
	TITLE : Microsoft Support Policy on Hardware Not On Windows NT HCL
	
	ARTICLE-ID: Q126690
	TITLE: Windows NT 4.0 Setup Troubleshooting Guide
	======================================================================
	Keywords          : kbsetup kbhowto 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT351search kbWinNT400search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS351search
	Version           : WinNT:3.51,4.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
