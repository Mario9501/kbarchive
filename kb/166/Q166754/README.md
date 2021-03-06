---
layout: page
title: "Q166754: Encarta 97: Insufficient Memory/Not Enough Free Memory"
permalink: /kb/166/Q166754/
---

## Q166754: Encarta 97: Insufficient Memory/Not Enough Free Memory

{% raw %}

	Article: Q166754
	Product(s): Microsoft Home Multimedia Titles
	Version(s): 1997
	Operating System(s): 
	Keyword(s): kbenv kberrmsg kbmm kbprb
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Encarta 97 Encyclopedia for Windows 
	- Microsoft Encarta Encyclopedia 97 Deluxe for Windows 
	- the operating system: Microsoft Windows versions 3.1, 3.11 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you start the 1997 edition Encarta encyclopedia in Windows 3.1, you receive
	an error message about not having enough memory. This occurs even if you the
	amount of RAM required by Encarta (at least 8 MB).
	
	The error message reads:
	
	  Insufficient Memory
	
	  There is not enough free memory to run Encarta 97 Encyclopedia. To correct
	  this situation:
	
	1. Close any other open applications and attempt to run Encarta Encyclopedia
	  again. If this dialog reappears, proceed to step 2.
	
	2. Increase the amount of free memory by modifying the Windows virtual memory
	  setting. For more information, click Help.
	
	NOTE: If you have at least 8 MB of RAM, you do not need to purchase more RAM
	memory to run Encarta 97.
	
	CAUSE
	=====
	
	This message is caused when the Windows swapfile (Virtual Memory setting) is too
	small.
	
	RESOLUTION
	==========
	
	To set a large enough swapfile, you may need to do the following (detailed
	instructions are included below this summary):
	
	- Free up RAM memory. You need at least 5,500 KB Extended Memory free in
	  MS-DOS, before starting Windows. A quick way to free up RAM memory is to
	  reduce the SmartDrive cache setting.
	
	  NOTE: Running MemMaker will not free up Extended memory. MemMaker is primarily
	  designed to configure Conventional Memory.
	
	- Change the swapfile settings in the Windows Control Panel. This needs to be
	  at least 10,000 KB for an 8 MB machine.
	
	- If the steps above do not help, free up hard drive space, and change the
	  swapfile settings again. Windows sizes the swapfile according to how much
	  hard drive space is available.
	
	Free Up RAM memory
	------------------
	
	To free up RAM memory, do the following:
	
	1. Exit Windows.
	
	2. Type the following at the MS-DOS command prompt, and then press ENTER:
	
	  mem
	
	3. NOTE: "Total" memory reported should be at least 8192 KB (8 MB). If it's not,
	  your computer does not meet the minimum system requirements, and you may need
	  to purchase more RAM memory.
	
	4. Note the Extended Memory Free figure. This should be at least 5,500 KB. If it
	  is, skip to step 6.
	
	5. If the "Extended Free" memory is less than 5,500 KB, you need to free up RAM
	  memory being used by MS-DOS programs or utilities.
	
	  SmartDrive commonly uses 2 MB of RAM, so reducing the cache size will often
	  solve the problem. Follow these steps:
	
	  a. At the MS-DOS prompt, enter the following command:
	
	     edit c:\autoexec.bat
	
	  b. Look for the line with the word "smartdrv" in it.
	
	  c. Add the following to the end of the line:
	
	     2048 1024
	
	     For example:
	
	     c:\windows\smartdrv /x 2048 1024
	
	     NOTE: The first number specifies a DOS cache of 2048 KB (2 MB) and the
	     second number specifies a Windows cache of 1024 KB (1 MB). If you have
	     Windows for Workgroups, you can use these numbers: 2048 256.
	
	  d. On the File menu, click Exit.
	
	  e. When you are prompted to Save changes, click Yes or press ENTER.
	
	  f. Reboot the computer.
	
	6. Start Windows and create a Swapfile as detailed below.
	
	Create Swapfile Of Sufficient Size
	----------------------------------
	
	To create a swapfile of sufficient size, follow these steps in Windows:
	
	1. From Program Manager, open the Windows Control Panel, usually located in the
	  Main program group.
	
	2. Double-click the Enhanced icon.
	
	3. Click the Virtual Memory button.
	
	4. NOTE: The Size listed in the Settings area. If this is 15,000 KB or more,
	  click Cancel. The swapfile is already large enough.
	
	  NOTE: Even larger swapfiles will allow you to run multiple programs at the
	  same time, such as Encarta and your Web browser. With the minimum required
	  swap file, you may be able to run only Encarta by itself.
	
	5. Click Change. A New Swapfile Settings area will appear at the bottom of the
	  window.
	
	6. In the New Swapfile Settings area, note the New Size field. This size needs
	  to be at least 10,000 KB for an 8MB machine.
	  NOTE: You may need more than 10,000 KB depending on your system
	  configuration.
	
	  WARNING: Do not change this New Size manually, as Windows will not use more
	  than the "recommended" size.
	
	7. If the New Size is too small, click the Type list and change it to Temporary.
	
	8. If the New Size is still too small, click the Drive list, and change it to
	  another drive (if available).
	
	  WARNING: Do not change to a compressed drive unless the Type is set to
	  Temporary.
	
	9. If the New Size is large enough, Click OK. When Windows asks you if you are
	  sure you want to make changes to the virtual memory settings, click Yes.
	  Windows now confirms the creation of the Swapfile. Click OK. When Windows
	  prompts you to restart, click Restart Windows.
	
	10. If the New Size is not large enough, click Cancel and free up more hard
	  drive space as detailed below.
	
	Free Up More Hard Drive Space
	-----------------------------
	
	You need at least 20 MB of available hard drive space to create a 10 MB swapfile
	(10,000 KB). This is because Windows will only use half of the available hard
	drive space as a swapfile. If you have less than 10 MB of free space, delete
	unnecessary files or uninstall unused programs from your hard drive. The easiest
	way to do this is:
	
	1. Uninstall Encarta. This will free up 10 MB. (Just double-click the Uninstall
	  Encarta 97 Encyclopedia icon).
	
	2. Set the swapfile size using the steps above.
	
	3. After successfully creating a larger swapfile, install Encarta again.
	
	MORE INFORMATION
	================
	
	If you continue to receive an Insufficient Memory error message after you try
	the steps in the "RESOLUTION" section above, make sure you do not have any
	unnecessary programs running or loading on your computer. Disabling screen
	savers or turning off high-resolution wallpaper may also help free up enough
	memory.
	
	To check the amount of actual free memory in Windows (free RAM + free Virtual
	Memory), do the following:
	
	1. On the Help menu in Program Manager, click About Program Manager.
	
	  NOTE: The Memory figure at the bottom of the About window. There needs to be
	  at least 14,000 to 15,000 KB free before Encarta will run.
	
	Adding more RAM memory (over 8 MB) will also increase this figure, but is not
	necessary to run Encarta. Increasing the size of the swapfile or preventing
	unnecessary programs from loading will also free enough memory.
	
	Additional query words: 1997 multi media multimedia multi-media mmtitles kbmm
	
	======================================================================
	Keywords          : kbenv kberrmsg kbmm kbprb 
	Technology        : kbOSWinSearch kbHomeProdSearch kbHomeMMsearch kbZNotKeyword6 kbEncartaSearch kbEncartaEncycSearch kbEncartaEnCyc1997 kbEncartaEnCyc1997Del kbOSWin310 kbOSWin311
	Version           : 1997
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
