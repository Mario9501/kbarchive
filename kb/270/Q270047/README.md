---
layout: page
title: "Q270047: Streets/MapPoint: Blue Screen When You Start Program"
permalink: /kb/270/Q270047/
---

## Q270047: Streets/MapPoint: Blue Screen When You Start Program

{% raw %}

	Article: Q270047
	Product(s): Microsoft Automap
	Version(s): 1.0
	Operating System(s): 
	Keyword(s): kb3rdparty kbdisplay kbenv kbimu
	Last Modified: 17-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MapPoint 2000 
	- Microsoft MapPoint 2001 
	- Microsoft MapPoint 2002 
	- Microsoft Expedia Streets and Trips 2000 
	- Microsoft Streets and Trips 2001 
	- Microsoft Streets & Trips 2002, version 1.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you start one of the programs listed at the beginning of this article or
	when you use the Search or Data Mapping features of the program, you may
	experience the following symptoms:
	
	- You receive a "fatal exception" error message on a blue screen.
	
	- Your computer restarts unexpectedly.
	
	You may also receive the following blue screen error message:
	
	  *** STOP: 0x00000050 (0xBFB54000, 0x00000000, 0xBFB2C08E, 0x00000000)
	  PAGEFAULT_IN_NONPAGED_AREA *** Address BFB2C08E base at BFB1A000, DateStamp
	  395db967 - nm2200dp.dll
	
	CAUSE
	=====
	
	This behavior can occur if both of the following conditions are true:
	
	- An ATI, Matrox, Intel or NeoMagic video adapter is installed in the computer.
	
	- The program is installed on a Microsoft Windows NT 4.0, Windows 2000, or a
	  Windows XP based computer.
	
	- This issue may also occur when performing a find in the program.
	
	
	
	WORKAROUND
	==========
	
	To resolve this issue, use the appropriate method for your version of Microsoft
	Windows.
	
	Windows 2000
	------------
	
	Reduce the graphics hardware acceleration setting:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click Display.
	
	3. On the Settings tab, click Advanced.
	
	4. Click the Troubleshooting tab.
	
	5. Move the Hardware Acceleration slider all the way to the left (the None
	  position), and then click OK.
	
	NOTE: If the issue continues to occur, reduce the Colors setting on the Settings
	tab of the Display Properties dialog box to 256 Colors, and then click OK.
	
	Windows NT 4.0
	--------------
	
	Reduce the color palette setting to 256 Colors:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click Display.
	
	3. Click the Settings tab.
	
	4. In the Color Palette box, click 256 Colors, and then click Test.
	
	5. Click OK, and then click Yes.
	
	6. Click OK, and then close Control Panel.
	
	NOTE: If reducing the color palette setting to 256 Colors resolves this issue,
	you can also attempt to increase the color palette setting to True Color (24
	bit) or True Color (32 bit).
	
	This has also been reported to resolve this issue.
	
	MORE INFORMATION
	================
	
	The third-party products discussed in this article are manufactured by vendors
	independent of Microsoft; we make no warranty, implied or otherwise, regarding
	these products' performance or reliability.
	
	Additional query words: mp2000 mp2001 est2000 st2001 map point crash quits reboot error log memory dump find mp2002 st2002
	
	======================================================================
	Keywords          : kb3rdparty kbdisplay kbenv kbimu 
	Technology        : kbHomeProdSearch _IKkbbogus kbExpediaSearch kbMapptSearch kbMapPoint2000 kbMapPoint2001 kbExpediaStreets2000 kbExpediaStreets2001 kbExpediaStreets2002 kbMapPoint2002
	Version           : :1.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
