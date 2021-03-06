---
layout: page
title: "Q136037: OLEDLG.DLL and MSVCRT20.DLL Not Found For Crystal Reports"
permalink: /kb/136/Q136037/
---

## Q136037: OLEDLG.DLL and MSVCRT20.DLL Not Found For Crystal Reports

{% raw %}

	Article: Q136037
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:1.1,3.5
	Operating System(s): 
	Keyword(s): kb3rdparty kbother
	Last Modified: 18-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 1.1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to run Crystal Reports version 3.0.1.29 included with Systems
	Management Server 1.1 in Windows NT 3.5, the following error message appears:
	
	  The dynamic link library OLEDLG.dll could not be found in the specified path
	  x:\CRW;<system paths>
	
	where x is the drive where Systems Management Server 1.1 is installed.
	
	The following error message appears when you choose OK:
	
	  The dynamic link library MSVCRT20.DLL could not be found in the specified
	  path x:\CRW;<system paths>
	
	where x is the drive where Systems Management Server 1.1 is installed.
	
	CAUSE
	=====
	
	Your OLEDLG.DLL and MSVCRT20.DLL files are not in the Crystal Reports directory
	or the system paths.
	
	RESOLUTION
	==========
	
	To correct this problem:
	
	- Upgrade to Windows NT 3.51.
	
	-or-
	
	- Reinstall the OLEDLG.DLL and MSVCRT20.DLL files into the correct
	  directories:
	
	  1. Copy OLEDLG.DL_ from the \I386 directory on the Windows NT 3.51 compact
	     disc to the \CRW directory or the %SystemRoot%\SYSTEM32 directory.
	
	  2. Run EXPAND.EXE to expand the compressed OLEDLG.DL_ file to the name
	     OLEDLG.DLL.
	
	  3. Copy the MSVCRT20.DLL file from the \DRVLIB\COMM\ECCI\X86 directory on the
	     Windows NT 3.51 compact disc to the \CRW directory or the
	     %SystemRoot%\SYSTEM32 directory.
	
	For additional information, contact Crystal Technical Support at (604) 669-8379.
	
	The third-party product discussed here is manufactured by a vendor independent of
	Microsoft; we make no warranty, implied or otherwise, regarding this product's
	performance or reliability.
	
	Additional query words: prodsms sms prodnt
	
	======================================================================
	Keywords          : kb3rdparty kbother 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTSsearch kbSMSSearch kbPocketIE110 kbMailPCN350
	Version           : winnt:1.1,3.5
	
	=============================================================================
	

{% endraw %}
