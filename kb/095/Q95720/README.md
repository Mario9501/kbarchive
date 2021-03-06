---
layout: page
title: "Q95720: How to Write to Windows-Style .INI Files"
permalink: /kb/095/Q95720/
---

## Q95720: How to Write to Windows-Style .INI Files

{% raw %}

	Article: Q95720
	Product(s): Microsoft FoxPro
	Version(s): 2.50 2.50a 3.00
	Operating System(s): 
	Keyword(s): kbcode
	Last Modified: 04-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	- Microsoft FoxPro for Windows, versions 2.5, 2.5a 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The following examples show how to write specific information to Windows- style
	.INI files. The first example shows how to write information to the WIN.INI
	file, and the second example shows how to write information to any other
	Windows-style .INI file.
	
	MORE INFORMATION
	================
	
	Example 1
	---------
	
	The following code will write to the Load= line in the [Windows] section of the
	WIN.INI file:
	
	
	     SET LIBRARY TO SYS(2004)+"FOXTOOLS.FLL"
	     MAPPNAME="WINDOWS"
	     MKEYNAME="LOAD"
	     MSETTING="CLOCK.EXE"
	     MREGISTER=REGFN("WRITEPROFILESTRING","CCC","I")
	     MCALL=CALLFN(MREGISTER,MAPPNAME,MKEYNAME,MSETTING)
	
	
	MAPPNAME points to an application heading in the WIN.INI file. In this case, it
	is pointing to the [Windows] application name.
	
	MKEYNAME points to a key name that appears under the application name. The above
	example points to the Load= line.
	
	MSETTING is the string that contains the value to be assigned to the key name.
	
	NOTE: The code in Example 1 puts CLOCK.EXE on the Load= line. It does not append
	CLOCK.EXE to any existing information for this key name. It simply replaces the
	value. If the Load= line was not present in the [Windows] section of the WIN.INI
	file, this code would have added it.
	
	MREGISTER is the variable name that defines the function using the RegFn
	function. The sample code above registers the function WriteProfileString and
	will write information to the WIN.INI file.
	
	MCALL is used to call the function defined in MREGISTER and pass it the
	appropriate parameters.
	
	To write to a different section of the WIN.INI, change the value of MAPPNAME to
	the appropriate application name. Also, change the MKEYNAME value to the key
	name that will hold the information, and change the MSETTING value to the
	setting to store in the selected key name.
	
	NOTE: The application name and key name are not case sensitive.
	
	Example 2
	---------
	
	The following code will change the COLOR SCHEMES= line in the [Current] section
	of the CONTROL.INI file:
	
	
	     SET LIBRARY TO SYS(2004)+"FOXTOOLS.FLL"
	     MAPPNAME="CURRENT"
	     MKEYNAME="COLOR SCHEMES"
	     MSETTING="FLUORESCENT"
	     MFILENAME="CONTROL.INI"
	     MREGISTER=REGFN("WRITEPRIVATEPROFILESTRING","CCCC","I")
	     MCALL=CALLFN(MREGISTER,MAPPNAME,MKEYNAME,MSETTING,MFILENAME)
	
	
	The commands are almost the same as those in Example 1, except that Example 2
	uses WritePrivateProfileString. This allows you to specify a Windows- style .INI
	file other than the WIN.INI file. One other difference is the addition of
	MFILENAME to specify the .INI file to write to. By default, if no path is
	specified, Windows will look in the Windows program directory for the .INI file.
	
	Additional query words: VFoxWin FoxWin 2.50
	
	======================================================================
	Keywords          : kbcode 
	Technology        : kbVFPsearch kbAudDeveloper kbFoxproSearch kbFoxPro250 kbFoxPro250a kbVFP300
	Version           : 2.50 2.50a 3.00
	
	=============================================================================
	

{% endraw %}
