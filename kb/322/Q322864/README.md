---
layout: page
title: "Q322864: Deleted Files Do Not Immediately Go Away"
permalink: /kb/322/Q322864/
---

## Q322864: Deleted Files Do Not Immediately Go Away

{% raw %}

	Article: Q322864
	Product(s): Microsoft Windows NT
	Version(s): 3.0
	Operating System(s): 
	Keyword(s): kbenv kbtool kbui
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows Services for UNIX, version 3.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	After you delete files from a location that is shared by Server For NFS, the
	files do not immediately go away. Although the file or files seem to remain, you
	cannot use the file or files.
	
	CAUSE
	=====
	
	NFS Server caches file handles for a period of time that is determined by the
	following two registry values:
	
	  RdWrHandleLifeTime
	  RdWrThreadLifeTime
	
	These values are located in the following registry key:
	
	  HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NfsSvr\Parameters
	
	The duration for which a handle stays in the cache beyond the time it was last
	accessed is the product of the preceding two values in seconds. By default, both
	values are set to 5, and this means a duration of 25 seconds.
	
	Formula
	-------
	
	  RdWrHandleLifeTime * RdWrThreadLifeTime = time handle stays in cache
	
	Example
	-------
	
	  5 * 5 = 25 seconds
	
	RESOLUTION
	==========
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	If server usage is predominantly done by using NFS, increase one or both of these
	values to improve performance:
	
	  RdWrHandleLifeTime
	  RdWrThreadLifeTime
	
	Microsoft does not recommend that you use a total duration of more than 100
	seconds because it may lead to extra caching of file handles on the server side.
	Too much caching may lead to too much memory and handle consumption.
	
	If the server is being used in a multi-mode environment (CIFS and NFS), leave the
	total duration as it is, or reduce it to a minimum of 10 seconds.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbenv kbtool kbui 
	Technology        : kbWinServiceUNIXSearch kbWinServiceUNIX300
	Version           : :3.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
