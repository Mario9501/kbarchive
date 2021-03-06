---
layout: page
title: "Q237843: HOWTO: Synchronize a SourceControlled VFP Project Between Users"
permalink: /kb/237/Q237843/
---

## Q237843: HOWTO: Synchronize a SourceControlled VFP Project Between Users

{% raw %}

	Article: Q237843
	Product(s): Microsoft SourceSafe
	Version(s): WINDOWS:5.0,5.0a,6.0
	Operating System(s): 
	Keyword(s): kbSSafe500 kbSSafe600 kbvfp kbvfp500 kbvfp500a kbvfp600 _IK kbGrpDSSSafe
	Last Modified: 01-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual SourceSafe for Windows, versions 5.0, 6.0 
	- Microsoft Visual FoxPro for Windows, versions 5.0, 5.0a, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When synchronizing changes made to a SourceCode Controlled Visual Fox Pro (VFP)
	project (.pjx) between multiple developers, you use different techniques
	depending on whether you are:
	
	- changing existing files.
	
	- adding or removing files.
	
	MORE INFORMATION
	================
	
	In the following scenarios, you need to assume that there are two users, userA
	and userB.
	
	Synchronizing changes to existing files:
	
	UserA checks out, modifies, then saves and checks in a file. To see the new
	version of the file, userB chooses "Get Latest Version" of that file.
	
	Microsoft Visual SourceSafe (VSS) does not provide a way of automatically
	notifying users when a file is checked in. If an automatic notification is
	desired, you should develop methods for providing that notification.
	
	For additional information, please click the article number below to view the
	article in the Microsoft Knowledge Base:
	
	  Q238556 HOWTO: Notify Other Team Members when Changing Projects Under Source
	  Controlled Projects
	
	In more complex scenarios, such as when multiple users may have the same files
	checked out simultaneously, all users should periodically refresh the project
	(From the Project menu select Refresh).
	
	You might also want to Show Differences on a file to compare your local copy with
	the latest version in VSS before "Getting Latest Version" from VSS, which would
	overwrite your local copy.
	
	Adding or removing files to or from a project:
	
	If userA adds files to (or removes files from) a project, from the
	Project->Source Control menu the userA selects "Update Project List. "UserB
	then updates his/her project list by choosing the menu items mentioned in the
	previous statement to see the changes made by userA.
	
	REFERENCES
	==========
	
	For additional information about Visual FoxPro and Visual SourceSafe
	integration, please see the following article(s) in the Microsoft Knowledge
	Base:
	
	  Q237847 INFO: The Role of the .pjm File in VSS / VFP Integration
	
	  Q157636 HOWTO: Set Up Source Code Control with Visual SourceSafe
	
	Additional query words: .pjm update
	
	======================================================================
	Keywords          : kbSSafe500 kbSSafe600 kbvfp kbvfp500 kbvfp500a kbvfp600 _IK kbGrpDSSSafe 
	Technology        : kbVFPsearch kbSSafeSearch kbAudDeveloper kbVFP500 kbVFP600 kbVFP500a kbSSafe600 kbSSafe500
	Version           : WINDOWS:5.0,5.0a,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
