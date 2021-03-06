---
layout: page
title: "Q304101: Backup Fails with Event ID 1450"
permalink: /kb/304/Q304101/
---

## Q304101: Backup Fails with Event ID 1450

{% raw %}

	Article: Q304101
	Product(s): Microsoft Windows NT
	Version(s): 2000,2000 SP1,2000 SP2,2000 SP3,4.0,4.0 SP1,4.0 SP2,4.0 SP3,4.0 SP4,4.0 SP5,4.0 SP6,4.
	Operating System(s): 
	Keyword(s): kbfaq
	Last Modified: 25-JUL-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 4.0, 4.0 SP1, 4.0 SP2, 4.0 SP3, 4.0 SP4, 4.0 SP5, 4.0 SP6, 4.0 SP6a 
	- Microsoft Windows NT Server, Enterprise Edition versions 4.0, 4.0 SP4, 4.0 SP5, 4.0 SP6, 4.0 SP6a 
	- Microsoft Windows versions 2000, 2000 SP1, 2000 SP2, 2000 SP3 Server 
	- Microsoft Windows versions 2000, 2000 SP1, 2000 SP2, 2000 SP3 Advanced Server 
	- Microsoft Windows versions 2000, 2000 SP2, 2000 SP3 Datacenter Server 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you 
	modify the registry, make sure to back it up and make sure that you understand how to restore 
	the registry if a problem occurs. For information about how to back up, restore, and edit the 
	registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	This article applies to both Microsoft-supplied backup programs and to
	third-party backup programs that use the NT backup application programming
	interface (API).
	
	When you run a backup program, the backup may not complete successfully. This may
	occur even if you run the program locally on the server. You may also receive
	the following error messages in the application log:
	
	  ERROR 1450: Insufficient system resources exist to complete the requested
	  service.
	
	  ERROR 1450: / hex 0x5aa ERROR_NO_SYSTEM_RESOURCES
	
	  Operating system error 1450 Insufficient system resources exist to complete
	  the requested service.
	
	  Write on "device" failed, status = 1450
	
	  ERROR 1130: Not enough server storage is available to process this command.
	
	  ERROR 1130 / hex 0x46a ERROR_NOT_ENOUGH_SERVER_MEMORY
	
	  Backup or restore operation terminating abnormally.
	
	Although it is unlikely, you may also receive the Event ID: 2020 and Event ID:
	2021 error messages from the server service.
	
	You may receive these error messages for reasons that are not related to the
	issue that this article addresses; however, if you receive these error messages
	only when you back up large system volumes, the two most probable causes are
	those that this article describes.
	
	One method that can be used to identify the problem is to start Task Manager and
	then click the Performance tab. At the bottom, locate the Kernel Memory section
	and watch the value for Paged Pool Memory. You may experience the problem when
	that value reaches approximately 160 MB (or larger on Windows 2000.) You will
	not experience this issue until a much higher value of paged pool is used if the
	key for paged pool has been set to a higher value (the issue may occur when the
	paged pool reaches about 80 percent of the set value.) If you have gflags turned
	on for pool tags and you use Poolmon, you will see higher usage of the MmSt tag,
	which is the pool tag that is used to map the operating system memory that is
	used to track shared files.
	
	CAUSE
	=====
	
	The two causes of this condition are related. The most common cause is listed
	first:
	
	- More files are open than the memory cache manager can handle. As a result,
	  the cache manager has used up the available paged pool memory.
	
	- The backup program has tried to back up a file whose size is larger than the
	  backup API can access on that version of the operating system. This has the
	  same result (that is, the paged pool is used up).
	
	Note that the resolution for each issue differs depending on whether you see the
	condition on Windows 2000 or Windows NT 4.0.
	
	RESOLUTION
	==========
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	Windows 2000
	------------
	
	NOTE: You must be using Service Pack 2 (SP2) or later. For additional information
	about why you must use Windows 2000 Service Pack 2, click the article number
	below to view the article in the Microsoft Knowledge Base:
	
	  Q259837 You May Not Be Able to Copy Large Files on Computers That Are Running
	  Windows NT 4.0 or Windows 2000
	
	Resolve the First Issue:
	
	You may have to change two registry settings. You must always change the first
	setting, and you also may have to change the second setting based on your
	configuration.
	
	Registry Setting 1
	
	1. Start Registry Editor (Regedt32.exe).
	
	2. Locate and then click the following key in the registry:
	
	  HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Session
	  Manager\Memory_Management
	
	3. On the Edit menu, click Add Value, and then add the following registry value:
	
	  Value name: PoolUsageMaximum
	  Data type: REG_DWORD
	  Radix: Decimal
	  Value data: 30
	
	IMPORTANT: Use 30 as your initial value. If your backup does not succeed, use 10
	as your value. If that does not work, you must change the behavior of your
	backup program to reduce the demand of paged pool. If the value works, you may
	want to increase the value by approximately 20 percent until the backup does not
	work. If the backup is unsuccessful, use the second registry setting that is
	described in this article.
	
	IMPORTANT: If you are running /3GB and or /PAE, use 10 as your initial setting.
	
	4. Quit Registry Editor.
	
	5. Restart your computer.
	
	Because you must test these settings during the most stressful backups, you may
	have to wait a month for a whole backup cycle to complete if you are not sure
	which backup consumes the most resources. Because of this, Microsoft recommends
	that you test low values first.
	
	For additional information, click the article number below to view the article in
	the Microsoft Knowledge Base:
	
	  Q312362 Server Is Unable to Allocate Memory from the System Paged Pool
	
	Registry Setting 2
	
	1. Start Registry Editor (Regedt32.exe).
	
	2. Locate and then click the following key in the registry:
	
	  HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Session
	  Manager\Memory_Management
	
	3. On the Edit menu, click Add Value, and then add the following registry value:
	
	  Value name: PagedPoolSize
	  Data type: REG_DWORD
	  Radix: Hex
	  Value data: 0xFFFFFFFF
	
	IMPORTANT: Setting PagedPoolSize to 0xFFFFFFFF (-1) allocates the maximum paged
	pool instead of other resources to the computer. This is typically required on a
	domain controller or a terminal server. By default, most Windows 2000 systems
	seem to be limited to a paged pool maximum size of 160 MB. You can verify this
	by downloading the kernel debuggers from the public Web site and opening a
	kernel dump in the debugger that you want to use. Note that the command to use
	is !vm, which shows a paged pool maximum of 163840 KB, for example. Adding this
	values reduces the Page Table Entries (PTEs) that are available on a system and
	extends the paged pool maximum to 343 MB.
	
	For additional information about why this value is necessary, click the article
	number below to view the article in the Microsoft Knowledge Base:
	
	  Q126402 PagedPoolSize and NonPagedPoolSize Values in Windows NT
	
	IMPORTANT: This value restricts the system PTEs that are available. PTEs are
	another unrelated system resource that your system uses. This setting may cause
	your system to display a blue screen with a stop 0x3F error when it starts. You
	can recover from this by using the last know good boot option on the system boot
	menu or recovery console. Use Performance Monitor to view the Free system page
	table entries counter. You can add the PagePoolSize setting if the observed free
	values are over 40,000.
	
	IMPORTANT: If you are running /3GB and /PAE together, do not set this setting
	without extensive testing and before you establish exactly how many system PTES
	you must have in your environment. You will probably see values in the range of
	10,000-20,000 free. Use the articles to configure paged pool memory but never
	drop below 10,000 free system PTEs.
	
	4. Quit Registry Editor.
	
	5. Restart your computer.
	
	For additional information about how to avoid and resolve this problem, click the
	article numbers below to view the articles in the Microsoft Knowledge Base:
	
	  Q256004 How to Troubleshoot 'STOP 0x3F' and 'STOP 0xD8' Error Messages in
	  Windows 2000
	
	  Q247904 How to Configure the Paged Address Pool and System Page Table Entry
	  Memory Areas
	
	Resolve the Second Issue:
	
	To resolve the second issue, make sure that SP2 or later is installed. If SP2 or
	later is installed and you still experience this issue, look for hotfixes on
	your system. If you have any post-SP2 hotfixes that have installed a new kernel,
	uninstall the fixes and then re-test your system. If this resolves your issue,
	run SP2 until a newer SP becomes available. For additional information about why
	SP2 is required, click the article number below to view the article in the
	Microsoft Knowledge Base:
	
	  Q259837 You May Not Be Able to Copy Large Files on Computers That Are Running
	  Windows NT 4.0 or Windows 2000
	
	Windows NT 4.0
	--------------
	
	NOTE: You must be using Service Pack 6a.
	
	For additional information, click the article number below to view the article in
	the Microsoft Knowledge Base:
	
	  Q171458 Windows NT May Fail On Request to Open Large Files
	
	Resolve the First Issue:
	
	1. Start Registry Editor (Regedt32.exe).
	
	2. Locate and then click the following key in the registry:
	
	  HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Session
	  Manager\Memory_Management
	
	3. On the Edit menu, click Add Value, and then add the following registry value:
	
	  Value name: UnusedFileCache
	  Data type: REG_DWORD
	  Radix: Decimal
	  Value data: 15
	
	NOTE: This number represents the percent of pool that can be consumed by unused
	segments. A value of 0 indicates that the system will use the default behavior
	that is similar to Windows NT 4.0 Service Pack 3. A value of 5 through 40
	indicates that the system will trim the unused file cache based on pool usage. 5
	is most aggressive (that is, it increases the size of the cache the least) and
	40 is least aggressive (that is, it lets the cache grow the largest before it
	trims the cache.)
	
	IMPORTANT: Use 15 as your initial value. If your backup does not succeed, use 5
	as your value. If this does not work, you must either change the behavior of
	your backup program to reduce the demand of paged pool, or you must upgrade to
	Windows 2000, where more than double the amount of paged pool is available (for
	more information, see the "Windows 2000" section). If this value works, you may
	want to increase it by approximately 20 percent until the backup is
	unsuccessful. If the backup is unsuccessful, use the second registry setting
	that is described in this article.
	
	IMPORTANT: If you are running /3GB and or /4GT, use 5 as your initial setting.
	
	4. Quit Registry Editor.
	
	5. Restart your computer.
	
	Because you must test these settings during the most stressful backups, you may
	have to wait a month for a whole backup cycle to complete if you are not sure
	which backup consumes the most resources. Because of this, Microsoft recommends
	that you test low values first.
	
	For additional information, click the article number below to view the article in
	the Microsoft Knowledge Base:
	
	  Q192409 Open Files Can Cause Kernel to Report INSUFFICIENT_RESOURCES
	
	Resolve the Second Issue:
	
	One possible resolution is to restrict the backup so that it backs up one file at
	a time. This may or may not work depending on the sizes of the files to be
	backed up. (It is expected to work on files that are smaller than 180 GB.) You
	can also try this resolution if you are backing up a few large files, but each
	file is smaller than 180 GB. Note that you must follow the steps to resolve the
	first problem also. For files larger than 180 GB, no workaround exists and you
	must upgrade the system to Windows 2000. If you try to back up the system
	remotely as a workaround, you will experience the same problem.
	
	1. Start Registry Editor (Regedt32.exe).
	
	2. Locate and then click the following key in the registry:
	
	  HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Session
	  Manager\Memory_Management
	
	3. On the Edit menu, click Add Value, and then add the following registry value:
	
	  Value name: DisablePagedPoolHint
	  Data type: REG_DWORD
	  Radix: Decimal
	  Value data: 1
	
	4. Quit Registry Editor.
	
	5. Restart your computer.
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in all versions of Microsoft
	Windows NT server and Microsoft Windows 2000 server.
	
	MORE INFORMATION
	================
	
	NTBackupread and NTBackupwrite both use buffered I/O. This means that Windows NT
	caches the I/O that is performed against the stream. It is also the only API
	that will back up the meta data of a file. This cache is pulled from limited
	resources: namely, pool and nonpaged pool. Because of this, extremely large
	numbers of files or files that are very large in size may cause the pool
	resources to run low.
	
	Several factors may use up the supply of paged pool memory. You can turn on pool
	tagging and take poolsnaps at different time intervals to help you to understand
	which driver is consuming paged pool memory. If the poolsnaps indicate that the
	MmSt tag (Mm section object prototype PTEs) is the largest consumer and is over
	80 MB, a very large number of files are probably open on the server.
	
	The possible maximum paged pool memory on a computer is 343 MB of paged pool in
	Windows 2000 with the paged pool key set to FFFFFFFF, or 164 MB if the key is
	not present. The possible maximum paged pool memory is 192 MB in Windows NT. By
	default, the Memory Manager tries to trim allocated paged pool memory when the
	system reaches 80 percent of the total paged pool. For example, 80 percent of
	343 MB number is 274 MB. If the Memory Manager cannot trim fast enough to keep
	up with the demand, the event that is listed in the "Symptoms" section of this
	article may occur. If you tune the Memory Manager to start the trimming process
	earlier (for example, when it reaches 40 percent), the computer can keep up with
	the paged pool demand during sudden peak usage so that it does not run out of
	paged pool memory.
	
	For additional information about the /3GB and /PAE switches, click the article
	number below to view the article in the Microsoft Knowledge Base:
	
	  Q283037 Large Memory Support Is Available in Windows 2000
	
	
	Additional query words:
	
	======================================================================
	Keywords          :  kbfaq
	Technology        : kbWinNTsearch kbWinNT400search kbwin2000AdvServ kbwin2000AdvServSearch kbwin2000DataServ kbwin2000DataServSearch kbwin2000Serv kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400sp6 kbWinNTSEnt400sp5 kbWinNTSEnt400sp4 kbWinNTSEnt400 kbWinNTS400sp6 kbWinNTS400sp5 kbWinNTS400sp4 kbWinNTS400sp3 kbWinNTS400sp2 kbWinNTS400sp1 kbWinNTS400search kbWinNTS400 kbwin2000ServSearch kbwin2000Search kbWinAdvServSearch kbWinDataServSearch kbWin2000AdvServSP2 kbWin2000AdvServSP1 kbWin2000DataServSP2 kbwin2000ServSP1 kbwin2000ServSP2 kbWinNTSEnt400SP6a kbWin2000AdvServSP3 kbWin2000DataServSP3
	Version           : :2000,2000 SP1,2000 SP2,2000 SP3,4.0,4.0 SP1,4.0 SP2,4.0 SP3,4.0 SP4,4.0 SP5,4.0 SP6,4.0 SP6a
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
