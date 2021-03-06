---
layout: page
title: "Q89724: Use New Disk Manager Drivers After MS-DOS Uninstall"
permalink: /kb/089/Q89724/
---

## Q89724: Use New Disk Manager Drivers After MS-DOS Uninstall

{% raw %}

	Article: Q89724
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:5.x,6.0,6.2,6.21,6.22
	Operating System(s): 
	Keyword(s): 
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 5.0, 5.0a, 6.0, 6.2, 6.21, 6.22 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	If you uninstall MS-DOS 5.0 or later on a machine that has been partitioned with
	Ontrack Disk Manager, you should continue to use the Disk Manager drivers
	supplied with the version of MS-DOS that you were using when you partitioned the
	disk. If you don't use these drivers, disk corruption can occur under certain
	circumstances.
	
	NOTE: This does not apply if the Disk Manager drivers are dated after the MS-DOS
	5.0 files.
	
	MORE INFORMATION
	================
	
	If you upgrade to MS-DOS 5.0 or later and have a partition that is larger than
	32 MB, Disk Manager updates the sector information so that it appears acceptable
	to MS-DOS. However, if you then uninstall MS-DOS to use an MS-DOS version prior
	to version 5.0 and you use the earlier Disk Manager drivers, the drivers are not
	MS-DOS version-aware, so they cannot reset the sector information automatically.
	This could cause disk or file corruption. The Disk Manager drivers supplied with
	MS-DOS versions 5.0 and later are MS- DOS version-aware.
	
	To avoid these kinds of disk problems, continue using the most current Disk
	Manager drivers.
	
	The product included here, Disk Manager, is manufactured by vendors independent
	of Microsoft; we make no warranty, implied or otherwise, regarding this
	product's performance or reliability.
	
	Additional query words: 6.22 5.00 5.00a 3rdparty 6.00 6.20
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS621 kbMSDOS622 kbMSDOS620 kbMSDOS600 kbMSDOS500 kbMSDOS500a
	Version           : MS-DOS:5.x,6.0,6.2,6.21,6.22
	
	=============================================================================
	

{% endraw %}
