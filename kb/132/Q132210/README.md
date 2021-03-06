---
layout: page
title: "Q132210: PC Win: Use of the Mail Utility PABSYNC.DLL"
permalink: /kb/132/Q132210/
---

## Q132210: PC Win: Use of the Mail Utility PABSYNC.DLL

{% raw %}

	Article: Q132210
	Product(s): Microsoft Mail For PC Networks
	Version(s): WINDOWS:3.2
	Operating System(s): 
	Keyword(s): 
	Last Modified: 12-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail for PC Networks, version 3.2 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes the purpose, installation, and operation of versions 3.0
	and 3.2 of Microsoft Mail for PC Networks utility PABSYNC.DLL that is included
	in the Microsoft Mail for PC Networks Resource Kit.
	
	Notes:
	
	- Until you fully understand the use of this program and as a precaution,
	  backup your mail message file (MMF) file.
	
	- You should use the utility with caution. While the program is useful in
	  synchronizing many of the Personal Address Book (PAB) inconsistencies with
	  the global address list (GAL), it is NOT effective in all situations.
	
	  For example, in a situation where you OK a change that will result in
	  duplicate entries in the PAB (both the friendly name and the address are the
	  same), the corrected entry will become unusable until the program is
	  restarted.
	
	- Because of the duplicate entries, you will also notice that the attempted
	  correction has not taken place. You should carefully review the changes
	  suggested by the program before accepting them.
	
	MORE INFORMATION
	================
	
	PABSync is a Microsoft Mail custom command that allows you to not only scan your
	PAB for inconsistencies, but also to interactively correct these
	inconsistencies.
	
	Installation
	------------
	
	PABSync consists of one dynamic-link library (DLL). This DLL, named PABSYNC.DLL,
	is installed into the Windows System directory. A new custom command entry is
	required in the MSMAIL.INI file located in the Windows directory. This line
	should look similar to the following:
	
	  PBS=3.0;File;P&AB Sync...;13;PABSYNC.DLL;2;;Synchronizes
	  personal addressbook;MSMAIL.HLP;2870
	
	Please refer to the Microsoft Mail documentation for additional information on
	installation of custom commands.
	
	Operation
	---------
	
	After PABSync is installed as a custom command, you can run it when Microsoft
	Mail for Windows is running. In order to use the utility, from the File menu,
	choose PAB Sync.
	
	PABSync will display a dialog box that asks you for the following:
	
	- whether you want to check your PAB for duplicate entries,
	
	- whether you want to check your PAB for inconsistencies against the GAL,
	
	- whether you want PABSync to automatically make corrections.
	
	NOTE: The automatic update of the PAB is disabled by default. Your input with
	this utility is desirable, and the automatic update feature should only be used
	if you fully understand its implications.
	
	Manual Update
	-------------
	
	After you check which types of synchronization you would like, PABSync proceeds
	to check for inconsistencies using the same method as the utility PABCheck
	(shipped with version 3.5 of Microsoft Mail for PC Networks.
	
	When you check for duplicate entries in the PAB, if one is found, a dialog box
	prompts you for confirmation of deletion of the duplicate entry. Then, you can
	select to either delete the duplicate entry or to ignore it. After you make your
	selection, the synchronization continues.
	
	When you check for invalid addresses, you can do two separate actions. If an
	entry is found that no longer matches the entry in the GAL (that is, the GAL has
	been updated and the PAB entry does not match the GAL entry), you are prompted
	with information about the updated entry and whether you would like to update
	your PAB. If you select to update your PAB, the synchronization continues.
	
	If you select to not update your PAB, then a second dialog box will prompt you
	for confirmation of deletion of the entry. You can either confirm the deletion
	or cancel it, and the synchronization will continue.
	
	Automatic Update
	----------------
	
	If in the initial selections menu you check for automatic updates, the PABSync
	utility will operate without prompting you for confirmation of any
	synchronization. Duplicate entries in the PAB will automatically be removed, and
	unsynchronized entries in the PAB with regard to the GAL will automatically be
	synchronized.
	
	During its operation, PABSync will log any inconsistencies that it finds and any
	transactions that occur. At the completion of the check and synchronization, the
	log will be placed into your Inbox in the form of a mail message. This operation
	is similar to that of PABCheck.
	
	Features such as automatic update of database or list entries can have their
	drawbacks, and PABSync's automatic synchronization features are no exception.
	Duplicate entries should not exist in the PAB. However, due to a limitation in
	the original versions of Mail for Windows (versions 3.0 and 3.2), it was
	possible to have duplicate entries added to a PAB. This has been corrected in
	maintenance releases. If the older client is being used, PABSync can be useful
	in detecting and correcting these duplicate entries. One-offs in the PAB are
	ignored as they are a feature that allows you to have entries without links to
	the GAL.
	
	Because it may be impossible to determine necessary information about the entry
	that will be updated, the inconsistencies between the PAB and GAL should be
	corrected manually. For example, if you have an entry with the friendly name
	John Doe in your PAB, John Doe leaves the company, and a new John Doe joins the
	company, an automatic resync will now have your PAB entry pointing to the new
	John Doe. If the user does not realize this, it will cause misdirected mail.
	
	For additional information, please see chapter 5 of the Microsoft Mail for PC
	Networks Resource Kit.
	
	
	Additional query words: 3.20 reskit five
	
	======================================================================
	Keywords          :  
	Technology        : kbMailSearch kbZNotKeyword3 kbMailPCN320
	Version           : WINDOWS:3.2
	
	=============================================================================
	

{% endraw %}
