---
layout: page
title: "Q322896: HOWTO: Prevent Scanning Specific File Types in Index Server"
permalink: /kb/322/Q322896/
---

## Q322896: HOWTO: Prevent Scanning Specific File Types in Index Server

{% raw %}

	Article: Q322896
	Product(s): Internet Information Server
	Version(s): 3.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Index Server version 3.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SUMMARY
	=======
	
	This article explains how to exclude a particular file type from being scanned
	and indexed, which can increase indexing performance by reducing the number of
	files that Index Server has to evaluate.
	
	MORE INFORMATION
	================
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	Index Server has to scan each file in a catalog even though the file may not be
	ultimately filtered. This can cause performance problems in some environments
	where a number of files exist that do not have to be scanned, but must remain in
	the catalog directory.
	
	To exclude certain file extensions from being scanned on a per catalog basis.
	Note that the catalog must be rebuilt, follow these steps:
	
	1. Start Regedit.exe.
	
	2. Select the following key:
	
	  HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\ContentIndex\Catalogs\YOURCATALOG\Scopes
	
	3. Add the following in the Scopes section:
	
	Name: *.tif
	Data Type: REG_SZ
	Data: ,,4
	
	4. Stop Indexing Service, and then delete the contents of the Catalog.wci
	  directory for your catalog.
	
	5. Restart Indexing Service and let the catalog build completely.
	
	REFERENCES
	==========
	
	For more information about the Index Server registry format, see the Microsoft
	Platform Software Development Kit (SDK).
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbIdxServSearch kbAudDeveloper
	Version           : :3.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
