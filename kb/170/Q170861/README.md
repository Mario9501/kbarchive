---
layout: page
title: "Q170861: Error 501, Not Supported When Using .Exe and .Com Applications"
permalink: /kb/170/Q170861/
---

## Q170861: Error 501, Not Supported When Using .Exe and .Com Applications

{% raw %}

	Article: Q170861
	Product(s): Internet Information Server
	Version(s): WinNT:2.0,3.0
	Operating System(s): 
	Keyword(s): kbother
	Last Modified: 02-MAY-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Server versions 2.0, 3.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you execute .Exe and/or .Com applications as scripts, the script will fail,
	and you will get the following error message:
	
	  Error 501, Not Supported.
	
	CAUSE
	=====
	
	When you use Internet Information Server (IIS) on Microsoft Windows NT Server
	version 4.0, Chapter 8 of the IIS documentation, the section titled "Associating
	Interpreters with Applications" lists the default interpreter for .Exe and .Com
	applications as "System". In other words, no interpreter should be defined for
	these applications.
	
	Because IIS gives you the ability to create applications in almost any
	programming language, IIS uses the file name extension to determine which
	interpreter to invoke for each application. These interpreters are defined in
	the registry at HKEY_LOCAL_MACHINE/
	System/CurrentControlSet/Services/W3SVC/Parameters/Script Map.
	
	The default interpreter for .Bat and .Cmd applications is Cmd.exe, and for .Idc
	the default interpreter is Httpodbc.dll. No script map should be defined for
	.Exe and .Com applications, as they are interpreted by the System.
	
	WORKAROUND
	==========
	
	WARNING: Using Registry Editor incorrectly can cause serious, system-wide
	problems that may require you to reinstall Windows NT to correct them. Microsoft
	cannot guarantee that any problems resulting from the use of Registry Editor can
	be solved. Use this tool at your own risk.
	
	If values for .exe and/or .com exist in HKEY_LOCAL_MACHINE/System/
	CurrentControlSet/Services/W3SVC/Parameters/Script Map delete them using the
	following steps:
	
	1. Start the Registry Editor (using Start, Run, Regedt32.exe).
	
	2. Locate the Script Map key at the following location:
	
	  HKEY_LOCAL_MACHINE/System/CurrentControlSet/Services/W3SVC/ 
	  Parameters/Script Map.
	
	3. Select the value for the .exe and/or .com interpreter.
	
	4. Click Delete on the Edit menu.
	
	5. When the value is removed, close the Registry Editor by selecting Registry,
	  Exit.
	
	6. Reboot the system.
	
	Additional query words: docerr
	
	======================================================================
	Keywords          : kbother 
	Technology        : kbiisSearch kbiis300 kbiis200
	Version           : WinNT:2.0,3.0
	Hardware          : ALPHA x86
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
