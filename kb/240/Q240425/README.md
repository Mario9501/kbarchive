---
layout: page
title: "Q240425: Zone Err Msg: Your Computer Is Trying to Update Your Zone Files"
permalink: /kb/240/Q240425/
---

## Q240425: Zone Err Msg: Your Computer Is Trying to Update Your Zone Files

{% raw %}

	Article: Q240425
	Product(s): Microsoft Home Games
	Version(s): 
	Operating System(s): 
	Keyword(s): kberrmsg kbimu msgamekbfaq
	Last Modified: 30-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Zone.com 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to load an Zone Web page, you may receive the following error
	message:
	
	  Your computer is trying to update your Zone files, but is receiving old
	  stored files from your ISP or network. Wait for your ISP or network to update
	  their files and try again later.
	
	NOTE: If the DownloadedVersion= line is blank when you click Details, click the
	following article number to view the article in the Microsoft Knowledge Base:
	
	  Q240952 Zone Error Message: Zone Setup Failed to Copy Itself to...
	
	CAUSE
	=====
	
	This behavior can occur if the Zone files available from your Internet service
	provider (ISP) or network are older than the files required by the Zone.
	
	RESOLUTION
	==========
	
	To resolve this issue, wait for your ISP or network to update their MSN Gaming
	Zone files.
	
	To ensure that outdated Zone files are not stored on your computer, use the
	appropriate method for your Web browser.
	
	Microsoft Internet Explorer 4.x or Later:
	
	1. On the View menu or Tools menu, click Internet Options.
	
	2. Under Temporary Internet Files, click Delete Files, and then click Yes or OK.
	
	3. Click Settings.
	
	4. Under "Check for newer versions of stored pages," click "Every time you start
	  Internet Explorer."
	
	5. Click OK, and then click OK again.
	
	6. Quit and then restart Internet Explorer.
	
	7. Connect to the Zone.
	
	Join a Different Game Room or Lobby:
	
	If the game you are play has multiple game rooms or lobbies, try joining a
	different one.
	
	MORE INFORMATION
	================
	
	If you are an Internet service provider (ISP) and you want to reduce the
	occurrence of this behavior, perform the following tasks:
	
	- Configure the proxy server to perform more update checks.
	- Configure the proxy server to perform more pre-fetching.
	- Reduce the Time to Live (TTL) setting for objects in the proxy server's
	  cache.
	- Filter the cache, so that objects originating from the following address are
	  not cached: http://fdl.msn.com/zone
	
	Additional query words: msgame igz msngz asheron's call ac
	
	======================================================================
	Keywords          : kberrmsg kbimu msgame kbfaq
	Technology        : kbGamesSearch kbMSNSearch kbZone
	Version           : :
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
