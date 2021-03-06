---
layout: page
title: "Q254189: Description of the Management Agent Working Folders"
permalink: /kb/254/Q254189/
---

## Q254189: Description of the Management Agent Working Folders

{% raw %}

	Article: Q254189
	Product(s): Microsoft Windows NT
	Version(s): 2.1
	Operating System(s): 
	Keyword(s): kbenv kbtool
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Metadirectory Services 2.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Management Agent (MA) working folders are created when the Management Agent is
	created in Microsoft Metadirectory Services (MMS). When you create an MA, you
	choose a descriptive name and the MA type from the predefined MAs included with
	MMS. A working folder with an 8-digit name is then created in the
	Zoomserver\Data\DS folder (for example Zoomserv\Data\DS\00000001). When you run
	the MA for the first time, the working folder is populated with intermediate and
	log files. The MA is initialized by using the contents of the
	Zoomserv\Data\Dsgate\<X> folder (where <X> is the MA type). Each MA
	creates a working folder. The files specified on the Working Folder tab may be
	unique based on the MA.
	
	To locate the working folder and MA-specific files:
	
	1. Click the MA.
	
	2. On the Action menu, click Properties.
	
	3. Click the "Intermediate Files and Logs Files" tab.
	
	4. Click the Working Folder tab. This tab lists the working folder and the files
	  associated with the MA.
	
	NOTE: The working folder is empty before you run the MA. Depending on the
	operational setting that you choose, the task to run depends on which files are
	written to the working folder when you run the MA.
	
	MORE INFORMATION
	================
	
	Because every MA is customized slightly for its corresponding connected folder,
	this example is based on the Microsoft Windows NT MA. This example demonstrates
	how to associate the working folder files with the operational setting for the
	MA.
	
	Microsoft Windows NT Management Agent Example
	---------------------------------------------
	
	The following MA processes are associated with the MA-specific files located in
	the working folder.
	
	  Groups Discovered: Import.ou
	  User Discovered: Import
	  Lists Discovered: Import.lst
	  CD Group Updates: Create
	  CD User Updates: Create.ou
	  CD List Updates: Create.lst
	  Foreign User Updates: Export
	
	Operational Settings for Microsoft Management Agents:
	
	The objects to process operational settings determine which files are created in
	the working folder.
	
	Types of Objects to Process:
	
	Process Windows NT Domains
	Process Windows NT Accounts
	Process Windows NT Groups
	
	MA Working Folders Considerations
	---------------------------------
	
	When you are making changes to the MA templates, it is important to understand
	the effects of making changes to the MA that is stored in the DSgate folder
	instead of the DS folder. The DSgate folder stores the initial copy that is used
	when the predefined MA is used to create an MA. Changing the MA in the Dsgate
	folder affects every MA created from that predefined MA. To change only one
	specific MA, change the MA that is stored in the DS folder.
	
	For additional information about predefined templates, click the article number
	below to view the article in the Microsoft Knowledge Base:
	
	  Q250312 Management Agents Included with Microsoft Metadirectory Services
	
	Additional query words:
	
	======================================================================
	Keywords          : kbenv kbtool 
	Technology        : kbMMSSearch kbMMS210
	Version           : :2.1
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
