---
layout: page
title: "Q303716: FP: Error Publishing/Saving File to Server Using Web Storage Sys"
permalink: /kb/303/Q303716/
---

## Q303716: FP: Error Publishing/Saving File to Server Using Web Storage Sys

{% raw %}

	Article: Q303716
	Product(s): Word Front Page
	Version(s): SP1
	Operating System(s): 
	Keyword(s): kbdta
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft FrontPage 2000 
	- Microsoft FrontPage 2002 
	- Microsoft Exchange 2000 Server SP1 
	- Microsoft SharePoint Portal Server 2001 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you 
	modify the registry, make sure to back it up and make sure that you understand how to restore 
	the registry if a problem occurs. For information about how to back up, restore, and edit the 
	registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	When you attempt to publish to or save a file to a Microsoft FrontPage extended
	Web on a server that is using the Web Storage System (Microsoft Exchange 2000
	Server or Microsoft SharePoint Portal Server), you receive one of the following
	error messages:
	
	  Cannot save file Filename.htm.
	
	  -or-
	
	  Cannot create file Filename.htm.
	
	CAUSE
	=====
	
	This problem can occur if either of the following conditions is true:
	
	- The Web you are connecting to is located on a Microsoft Exchange 2000 server
	  that is only one level below the root folder--for example,
	  http://<servername>/<public>/ where <servername> is the
	  name of the server you are connecting to and <public> is the name of
	  the virtual directory on the server. You cannot have sites in a Web Storage
	  System at the root of a folder tree.
	
	- The Web you are connecting to is located in a path on a Microsoft SharePoint
	  Portal Server that isn't accessible from Windows Explorer.
	
	  NOTE: On a default installation of SharePoint Portal Server, the path is:
	
	  \\.\backofficestorage
	
	RESOLUTION
	==========
	
	To correct this problem, use either of the following methods.
	
	Microsoft Exchange 2000 Server
	------------------------------
	
	Configure and connect to a Web located one level lower in the directory
	structure. For example, connect to http://servername/public/webname.
	
	To configure the Frontpage Server Extensions for the new Web, follow these
	steps:
	
	1. Open the Microsoft Management Console (MMC) for Internet Information Services
	  (IIS).
	
	2. Right-click the public level in the http://servername/public/webname path,
	  point to New, and then click Server Extensions Web.
	
	The New Web Wizard starts so that you can create a new Web at a lower level. Use
	unique permissions and specify an administrator for the new Web.
	
	Microsoft SharePoint Portal Server:
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	Permanently mount the server drive to a drive letter that is recognized by
	Windows Explorer. To do this, follow these steps:
	
	1. On the Windows Start menu, click Run.
	
	2. In the Open box, type "regedit" (without the quotation marks), and then click
	  OK.
	
	3. Locate and click the following registry key:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\EXIFS\Parameters
	
	4. In the Details pane, double-click Drive Letter.
	
	5. In the Value data box, type "<driveletter>" (without the quotation
	  marks), where <driveletter> is any available drive.
	
	6. Quit Registry Editor.
	
	7. Restart the server.
	
	Create a folder in the Web Storage System to contain the virtual directory that
	will be the FrontPage Web. To do this, follow these steps:
	
	1. Start Windows Explorer by right-clicking the Windows Start menu and then
	  clicking Explore on the menu that appears.
	
	2. Locate and select the following folder:
	
	  <driveletter>:\localhost\SharePoint Portal Server
	
	3. Create a new folder. To do this, point to New on the File menu and then click
	  Folder. Type a name for the new folder and press ENTER.
	
	4. Start the MMC for IIS.
	
	5. Right-click Default Web Site, point to New, and then click Virtual Directory.
	
	6. Create the virtual directory and point to the folder you created in step 3.
	
	7. Configure the Server Extensions for the new virtual Web. To do this,
	  right-click the new virtual directory, point to New, and then click Server
	  Extensions Web.
	
	NOTE: Configure the Web to use a different administrator than the parent Web.
	
	MORE INFORMATION
	================
	
	The instructions in the "Notes and Tips" topic in the Add-in for Web Storage
	System Forms (Exfp.chm) Help file incorrectly state that you can configure the
	extensions at the root of an alternate public folder tree. To connect to an
	Exchange Public Folder, you must have a path that is at least two levels deep,
	such as:
	
	  http://servername/public/webname
	
	Microsoft Visual Interdev or Microsoft FrontPage 98 cannot connect to these Webs
	because they do not allow connections to Webs at this depth. However, you can
	use Visual Interdev and Frontpage 98 to connect to the Root Web at
	http://servername.
	
	Additional query words: prb front page
	
	======================================================================
	Keywords          : kbdta 
	Technology        : kbFrontPageSearch kbSharePtPortalSvr2001 kbSharePtPortalSvrSearch kbExchangeSearch kbFrontPage2002 kbFrontPage2000Search kbFrontPage2002Search kbExchange2000Search kbZNotKeyword5 kbExchange2000Serv kbExchange2000ServSP1
	Version           : :SP1
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
